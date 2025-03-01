# Настройка работы сервисов Оркестратора с RabbitMQ через SSL

Данная статья содержит следующие подразделы:

1.	Заведение OpenSSL сертификатов для работы через SSL.
2.	Настройка RabbitMQ на Linux для работы через SSL.
3.	Настройка RabbitMQ на Windows для работы через SSL.
4.	Настройка сервисов оркестратора для работы с RabbitMQ через SSL.
5.	Полезные ссылки.

## Заведение OpenSSL сертификатов для работы через SSL

1. Устанавливаем OpenSSL либо с [официального сайта](https://www.openssl.org/), либо используем ту версию, что идет в составе одной из утилит (например, можно использовать ту, которая идет в составе git).
2. Для того, чтобы в скриптах каждый раз не использовать полный путь к файлу openssl.exe, рекомендуется добавить этот путь в настройки системной переменной Path (если же вы предпочитаете работать через PowerShell, а не через командную строку, и не желаете изменять системную переменную Path, то можно использовать сеансовые алиасы). 
3. Далее в данном руководстве предполагается, что полный путь прописан в системной переменной Path. 
4. Прописать путь в Path, если вы работаете в Windows,  можно таким образом:
Открываем указанное ниже диалоговое окно (и далее выбираем соответствующие вкладки / нажимаем указанные кнопки / выбираем указанные строки из списков): 
* В нерусифицированной версии Windows:  
`System Properties > Advanced > Environment Variables… > System variables > Path > Edit… > New > [Тут указываем полный путь к файлу openssl.exe]:`
* В русской версии Windows:  
`Свойства системы > Дополнительно > Переменные среды… > Системные переменные > Path > Изменить… > Создать > [Тут указываем полный путь к файлу openssl.exe]:`

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-1.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-2.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-3.PNG)

5. Далее создаем каталог, в котором будут размещаться как сами сертификаты, так и необходимые для их создания файлы и переходим в него.
6. RabbitMQ должен при запуске иметь доступ к корневому сертификату СА, сертификату сервера и приватному ключу сертификата сервера. Создадим эти файлы.
7. Первым делом создаем корневой ключ CA и затем создаем корневой сертификат CA.  
Для этого открываем командную строку и выполняем в ней такие 2 команды:
```
openssl genrsa -out RMQ-CA-Key.pem

openssl req -new -key RMQ-CA-Key.pem -x509 -days 10000 -out RMQ-CA-cert.pem
```
Заполняем необходимые поля для сертификата. Имена выбираем произвольно. На этом корневой сертификат CA создан.

8. Генерируем ключ для сервера:
```
openssl genrsa -out RMQ-server-key.pem 2048
```
9. Теперь создаем запрос на сертификат сервера. 
```
openssl req -new -key RMQ-server-key.pem -out RMQ-signingrequest.csr
```
При заполнении полей, в поле *Common Name* важно указать имя сервера: домен или IP адрес сервера (например домен: `db.example.com` или IP-адрес: `192.168.0.116`):
10. Генерируем самоподписанный x509-сертификат сервера используя запрос на сертификат сервера, сертификат СА и ключ сертификата СА:
```
openssl x509 -req -days 1000 -in RMQ-signingrequest.csr -CA RMQ-CA-cert.pem -CAkey RMQ-CA-Key.pem -CAcreateserial -out RMQ-server-cert.pem
```
11. Теперь таким же образом (как описано в трех предыдущих пунктах) создаем связку ключ-сертификат для клиента. Имена файлов соответственно меняем (например: `RMQ-client-key.pem`, `RMQ-client-signingrequest.csr`, `RMQ-client-cert.pem`):
```
openssl genrsa -out RMQ-client-key.pem 2048

openssl req -new -sha256 -key RMQ-client-key.pem -out RMQ-client-signingrequest.csr

openssl x509 -req -days 1000 -in RMQ-client-signingrequest.csr -CA RMQ-CA-cert.pem -CAkey RMQ-CA-Key.pem -CAcreateserial -out RMQ-client-cert.pem
```
При заполнении полей сертификата клиента, в поле *Common Name* указываем логин под которым будет выполняться подключение к RabbitMQ (по умолчанию для сервисов Оркестратора это имя: `admin` – далее во всех скриптах в этом руководстве подразумевается, что было задано именно такое имя для этого параметра).
12. Для работы с RabbitMQ клиентам требуется специальный тип сертификата PKCS12, создаем его такой командой:
```
openssl pkcs12 -export -out client-identity.p12 -inkey RMQ-client-key.pem -in RMQ-client-cert.pem
```
13. При этом запоминаем (записываем) парольную фразу, требуемую для данного типа сертификатов. Она нам пригодится в дальнейшем при конфигурировании работы сервисов Оркестратора.
14. В итоге в нашей рабочей папке должно быть 10 таких файлов:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-4.PNG)

15. Теперь переходим к настройке RabbitMQ и сервисов оркестратора для работы через SSL, как описано далее в настоящем руководстве


## Настройка RabbitMQ на Linux для работы через SSL

1. Копируем корневой сертификат CA, ключ и сертификат сервера (созданные ранее в п.1. настоящего руководства) в удобный для вас каталог (допустим, он расположен по такому пути: `/etc/pki/tls`). 
2. В итоге в этом каталоге должны быть установлены указанные выше файлы с такими правами:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-.PNG)

3. Теперь переходим к правке файла конфигурации RabbitMQ. Он должен быть собран с поддержкой SSL/TLS. Этот файл может по разному именоваться и может иметь разное расширение.
4. Расположение всех конфигурационых файлов можно найти запустив в командной строке команду:
```
rabbitmq-diagnostics status
```
Конфигурационные файлы будут перечислены в секции Config files:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-6.PNG)

5. Расположение конфигурационных файлов также можно найти, если кликнуть по кнопке с названием текущего узла в RabbitMQ management UI (в примере, показанном на картинке, следует кликнуть по кнопке с наименованием rabbit@astra-linux):

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-7.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-8.PNG)

6. Если конфигурационный файл имеет расширение *.config, то изменяем его в соответствии с описанием по настройке SSL в RabbitMQ для операционной системы Windows данного руководства.
7. Если этот файл имеет расширение *.conf, то для работы RabbitMQ через SSL/TLS вносим в него такие строки, подставив актуальные пути к сертификатам и ключу:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-9.PNG)

Если нам необходимо, чтобы RabbitMQ работал исключительно только через SSL/TLS, то следует внести в конфигурационный файл такие строки:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-10.PNG)

В нашем случае эта секция конфигурационного файла выглядит таким образом:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-11.PNG)

8. Следующий шаг: необходимо активировать встроенный в RabbitMQ плагин для аутентификации через SSL. Сделать это можно, выполнив в командной строке такую команду: 
```
rabbitmq-plugins enable rabbitmq_auth_mechanism_ssl
```
9. После этого необходимо перезагрузить сервис RabbitMQ. Сделать это можно, выполнив в командной строке такие 2 команды:
```
rabbitmq-service stop

rabbitmq-service start
```
10. Теперь проверяем, что мы все сделали правильно, и сервис RabbitMQ может работать через SSL/TLS. Запускаем RabbitMQ management UI и проверяем, что запущен SSL-порт 5671

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-12.PNG)

Затем, кликнув по кнопке с названием текущего узла, проверяем, что запущен плагин для работы через SSL и включен механизм аутентификации EXTERNAL:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-13.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-14.PNG)


## Настройка RabbitMQ на Windows для работы через SSL

1. Копируем корневой сертификат CA, ключ и сертификат сервера (созданные ранее в п.1. настоящего руководства) в удобный для Вас каталог (допустим он расположен по такому пути: `C:/tmp/certs`).
2. В итоге в этом каталоге должны быть установлены указанные выше файлы:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-15.PNG)

3. Теперь переходим к правке файла конфигурации RabbitMQ. Он должен быть собран с поддержкой SSL/TLS. Этот файл может по разному именоваться и может иметь разное расширение.
4. Расположение всех конфигурационых файлов можно найти, запустив в командной строке команду:
```
rabbitmq-diagnostics status
```
Конфигурационные файлы будут перечислены в секции Config files:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-16.PNG)

5. Расположение конфигурационных файлов также можно найти, если кликнуть по кнопке с названием текущего узла в RabbitMQ management UI (в примере, показанном на картинке, следует кликнуть по кнопке с наименованием rabbit@Victor-PC):  

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-17.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-18.PNG)

6. Если конфигурационный файл имеет расширение *.conf, то изменяем его в соответствии с описанием по настройке SSL в RabbitMQ для операционной системы Linux данного руководства.
7. Если этот файл имеет расширение *.config, то для работы RabbitMQ через SSL/TLS вносим в него такие строки, подставив актуальные пути к сертификатам и ключу:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-19.PNG)

Если нам необходимо, чтобы RabbitMQ работал исключительно только через SSL/TLS, то следует внести в конфиг такие строки:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-20.PNG)

8. Следующий шаг: необходимо активировать встроенный в RabbitMQ плагин для аутентификации через SSL. Сделать это можно, выполнив в командной такую команду:
```
rabbitmq-plugins enable rabbitmq_auth_mechanism_ssl
```
9. После этого необходимо перезагрузить сервис RabbitMQ. Сделать это можно, выполнив в командной строке с правами администратора такие 2 команды:
```
rabbitmq-service stop

rabbitmq-service start
```
10. Теперь проверяем, что мы все сделали правильно, и сервис RabbitMQ может работать через SSL/TLS. Запускаем RabbitMQ management UI и проверяем, что запущен SSL-порт 5671:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-21.PNG)

Затем, кликнув по кнопке с названием текущего узла, проверяем, что запущен плагин для работы через SSL и включен механизм аутентификации EXTERNAL:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-22.PNG)

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-23.PNG)


## Настройка сервисов Оркестратора для работы с RabbitMQ через SSL

1. Копируем специальный тип сертификата PKCS12 (созданный ранее в п.1. настоящего руководства) в удобный для вас каталог на машине, где развернут требуемый сервис Оркестратора. 
2. Далее меняем конфигурационный файл сервиса (файл appsettings.ProdWin.json для машин семейства Windows, или appsettings.ProdLinux.json  для машин семейства Linux). Для этого изменяем секцию RabbitMQ конфигурационного файла таким образом:
* Для параметра `Port` указываем значение `5671`. 
* Для параметра `UseSsl` указываем значение `true`.
* Для параметра `SslServerName` указываем имя сервера, которое было указано в сертификате сервера для RabbitMQ (см. п.1. данного руководства).
* Для параметра `SslCertPath` указываем полный путь и имя клиентского сертификата PKCS12.
* Для параметра `SslCertPassphrase` указываем парольную фразу, которую мы задали для сертификата PKCS12, когда его создавали (см. п.1. данного руководства).

3. Например, для машин с ОС Windows эти секции конфигурационнго файла могут выглядеть так:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-24.PNG)

4. Эти же секции конфигурационного файла для машин с ОС Linux могут выглядеть так:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-25.PNG)

5. Перед тем как запустить сервис Оркестратора, рекомендуется выставить в конфигурационном файле этого сервиса уровень логирования в Information, это поможет быстрее разобраться с возможными проблемами при его некорректном запуске. 
Например, как показано в данном случае:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-26.PNG)

6. Если все сконфигурировано корректно, то после запуска сервиса в его логах отобразится запись, что коннект с RabbitMQ установлен:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-27.PNG)

При этом в RabbitMQ management UI на вкладке Connections можно будет увидеть вновь созданный коннект:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-28.PNG)

И если кликнуть по названию этого коннекта, то можно получить его детальные характеристики:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-29.PNG)

7. Если же в конфигурационном файле сервиса что-то не устроит RabbitMQ, то в логах будет отображена детальная информация о том, что конкретно не так, как требуется. 

Например, вот что будет в логах, если в конфигурационном файле указан сертификат, подписанный каким-либо другим центром сертификации:
 
![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-30.PNG)

Или вот что будет в логах, если в конфигурационном файле указана некорректная парольная фраза для сертификата:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-31.PNG)

8. Если возникли совсем непонятные проблемы с SSL-сертификатом, то также будет полезно посмотреть логи самого RabbitMQ. Расположение этих логов можно узнать из RabbitMQ management UI кликнув по названию текущего узла:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/rabbit-ssl-32.PNG)


## Полезные ссылки

1. Сайт [OpenSSL](https://www.openssl.org/)
2. Документация по [сетевым настройкам RabbitMQ](https://www.rabbitmq.com/networking.html) (включая SSL/TLS, на английском языке) 
3. Документация по [настройкам TLS в RabbitMQ](https://www.rabbitmq.com/ssl.html) (на английском языке) 
4. Описание [кодов ошибок](https://techcommunity.microsoft.com/t5/iis-support-blog/ssl-tls-alert-protocol-and-the-alert-codes/ba-p/377132) при работе с SSL/TLS (на английском языке)
5. Описание [параметров rabbitmq.conf](https://github.com/rabbitmq/rabbitmq-server/blob/main/deps/rabbit/docs/rabbitmq.conf.example) (на английском языке) 
6. Описание [механизма аутентификации](https://github.com/rabbitmq/rabbitmq-auth-mechanism-ssl) с использованием x509 (TLS/SSL) сертификатов для RabbitMQ (на английском языке)
7. Реализация [аутентификации RabbitMQ](https://www.cshelton.co.uk/blog/2019/12/18/rabbitmq-client-certificate-authentication/) с использованием SSL/TLS по стандарту .NET Standard 2.1 (на английском языке)



