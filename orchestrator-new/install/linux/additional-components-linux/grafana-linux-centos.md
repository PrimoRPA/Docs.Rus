# Установка и настройка Grafana под CentOS 8

Grafana используется для построения интерактивных отчетов по временным рядам журналов Оркестратора и Робота с визуализацией результата в виде различных диаграмм. 

Grafana – отдельное приложение с веб-интерфейсом, работающее как служба Windows. По умолчанию служба слушает 3000 порт. Вовне этот порт не открывается, обращение к Grafana осуществляется через Front (nginx или IIS). Опционально Front может устанавливать для Grafana заголовок авторизации, чтобы не требовалось вводить логин и пароль.

Схема интеграции Grafana с Оркестратором:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-1.PNG)

Согласно иллюстрации выше интеграция с Grafana осуществляется следующим образом:
1.	Устанавливается приложение Grafana. Например, на том же сервере, где и WebApi.
2.	Средствами интерфейса Grafana настраивается источник данных для отчетов – БД ltoolslogs с журналами Оркестратора и Робота.
3.	Настраивается конфигурационный файл Grafana (для возможности настроить проксирование через Front, который является общим с Оркестратором).
4.	Создается ApiKey, который прописывается далее в конфигурационном файле nginx (не обязательный шаг).
5.	Настраивается проксирование с установкой заголовка авторизации в Front. Как было сказано выше, настройка заголовка авторизации необязательна. (В некоторых случаях нежелательна, так как ослабляет безопасность.)
6.	Средствами интерфейса Grafana создаются или импортируются отчеты\*, отчеты публикуются. При публикации отчетов Grafana формирует внешние ссылки на них. Возможно, некоторые отчеты потребуют создания view в БД.
7.	Ссылки на опубликованные отчеты добавляются в конфигурационный файл WebApi, чтобы они открывались через интерфейс Оркестратора. Больше никакой связи Оркестратор с Grafana не имеет.

> \* - Документация по созданию отчетов (дашбордов в терминах Grafana) находится на [официальном сайте Grafana](https://grafana.com/). Там же можно скачать дистрибутив с последней версией Grafana.

## Установка Grafana

Далее предполагается, что Grafana устанавливается на сервере Оркестратора.

Установочный файл Grafana идет в комплекте поставки. Также он может быть скачан с [официального сайта Grafana](https://grafana.com/), командой: 
```
$ wget https://dl.grafana.com/oss/release/grafana-7.3.4-1.x86_64.rpm
```
1. Запускаем установку: 
```
$ sudo dnf -y localinstall grafana-7.3.4-1.x86_64.rpm
$ sudo systemctl daemon-reload
$ sudo systemctl enable --now grafana-server
```
2. Проверяем, что служба Grafana работает: 
```
$ sudo systemctl status grafana-server
```
3. Открываем порт 3000:
```
$ sudo firewall-cmd --add-port=3000/tcp --permanent
$ sudo firewall-cmd --reload
```
4. Никакого специального интерфейса для управления этой службой у Grafana нет.

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-2.PNG)

5. Заходим в веб-интерфейс Grafana по адресу `http://localhost:3000` и вводим логин. со встроенной учетной записью admin/admin:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-3.PNG)

6. Меняем пароль по умолчанию на новый (Grafana сама предложит это сделать):

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-4.PNG)

7. Откроется панель управления Grafana. Установка Grafana завершена:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-5.PNG)

## Настройка источника данных для отчетов

Переходим в раздел Configuration/Data Sources. Для только что установленной Grafana можно перейти из раздела General/Home. Можно воспользоваться левым боковым меню «шестеренка»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-6.PNG)

Выбираем поставщика данных PostgreSQL или Microsoft SQL Server (в зависимости от вендора БД Оркестратора):

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-7.PNG)

Настраиваем подключение к БД ltoolslogs:

**Для PostgreSQL**:
* Name – оставляем по умолчанию PostgreSQL (можно выбрать произвольное);
* Host – IP-адрес и порт сервера БД (уточнить в конфигурационном файле WebApi);
* Database – ltoolslogs;
* User/Password – пользователь/пароль БД (уточнить в конфигурационном файле WebApi);
* TLS/SSL Mode – disable;
* Connection limits – все параметры этого блока оставляем по умолчанию;
* Version – 12;
* TimescaleDB\* – false;
* Min time interval – оставляем по умолчанию 1m; 

> \* - Grafana поддерживает TimescaleDB, что находит свое отражение при создании отчетов. За подробной информацией необходимо обратиться к официальной документации на официальном сайте Grafana.

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-8.PNG)

**Для Microsoft SQL Server**:
* Name – оставляем по умолчанию Microsoft SQL Server (можно выбрать произвольное);
* Host – IP-адрес (или имя хоста) и порт сервера БД (уточнить в конфигурационном файле WebApi);
* Database – ltoolslogs;
* Authentication – SQL Server Authentication
* User/Password – пользователь/пароль БД (уточнить в конфигурационном файле WebApi);
* Encrypt – false;
* Connection limits – все параметры этого блока оставляем по умолчанию;
* Min time interval – оставляем по умолчанию 1m;

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-9.PNG)

Внизу формы настройки подключения нажимаем кнопку «Save & test»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-10.PNG)

Если все сделано верно и БД ltoolslogs доступна, отобразится сообщение об удачном подключении к БД:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-11.PNG)

В разделе Configuration/Data Sources будет отображаться созданное подключение с наименованием PostgreSQL (Microsoft SQL Server):

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-12.PNG)

## Настройка конфигурационного файла Grafana

В WordPad (или аналогичной программе, **не Notepad!**) открываем конфигурационный файл Grafana `C:\Program Files\GrafanaLabs\grafana\conf\defaults.ini`.

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-13.PNG)

В секции [server] (можно найти поиском по файлу, Ctrl + F) меняем дефолтные значения параметров на:
```
root_url = %(protocol)s://%(domain)s:%(http_port)s/grafana/
serve_from_sub_path = true
```
Сохраняем файл и перезапускаем службу Grafana:
```
$ sudo systemctl restart grafana-server
```

## Создание Api Key (необязательно)

ApiKey создается в интерфейсе Grafana в разделе Configuration/Api keys (боковое левое меню «шестеренка»). Кликаем по кнопке «New API key»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-14.PNG)

Задаем параметры нового ApiKey:
* Key name – key1 (произвольное наименование на латинице);
* Role – оставляем по умолчанию Viewer (только просмотр);
* Time to life – 1000d. Время в днях, через которое ApiKey станет неактивным, и авторизация посредством него работать перестанет. Выбирать следует большим.

Нажимаем кнопку «Add»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-15.PNG)

Сохраняем где-то отдельно полученный ApiKey, так как через интерфейс Grafana увидеть его больше будет невозможно:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-16.PNG)

Закрываем модальное окно с новым ApiKey. Этот ApiKey под наименованием key1, которое ему дали ранее, будет отображаться в списке всех ApiKey:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-17.PNG)

## Настройка Front

### nginx

Открываем файл `C:\Primo\nginx-1.21.1\conf\nginx.conf` и добавляем следующие правила:

После секции upstream app_server добавляем секцию
```
upstream grafana {
        server localhost:3000;
}
```

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-18.PNG)

После правила перенаправления location/api/ добавляем правило
```
location /grafana/ {
            proxy_set_header Authorization "Bearer {ApiKey}";            
            proxy_pass http://grafana;                        
}
```
ApiKey (без фигурных скобок) подставляем созданный в раделе выше. 

Если не нужна автоматическая авторизация в Grafana, заголовок proxy_set_header Authorization можно не устанавливать (удалить всю строку).

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-19.PNG)

Из cmd перезапускаем nginx:
```
C:\Primo\nginx-1.21.1>nginx -s reload
```

### IIS

Добавляем серверную переменную AUTHORIZATION:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-20.PNG)

Открываем файл C:\Primo\UI\web.config и добавляем следующее правило после правила «Reverse Proxy to API»:
```
<rule name="Grafana" stopProcessing="false">
                <match url="^grafana(.*)" />
                <action type="Rewrite" url="http://localhost:3000/grafana{R:1}" />
                <serverVariables>
                      <set name="AUTHORIZATION" value="Bearer eyJrIjoickxTcUFDTWVvajlGNVVBT3pDUUxtQXBhMHFRbmVrOEEiLCJuIjoia2V5MSIsImlkIjoxfQ==" />
                </serverVariables>
 </rule>
```

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-21.PNG)

## Создание или импорт отчетов

Создание отчетов – отдельная большая тема. Для этого требуется, как минимум:
* владение средствами Grafana;
* владение SQL, в частности, его диалектом для PostgreSQL или Microsoft SQL Server и 
SQL-образным DSL Grafana;
* понимание структуры и семантики данных БД ltoolslogs.

Поэтому для примера рассмотрим импорт готового отчета в Grafana. 

Вообще говоря, наличие view в БД для отчетов в Grafana необязательно. Но для этого примера потребуется создать view – v_AllWorked-postgres (или v_AllWorked-mssql). Скрипт создания v_AllWorked-postgres.sql (v_AllWorked-mssql.sql) включен в поставку. Этот скрипт требуется выполнить в БД ltoolslogs.

Для импорта отчета переходим в раздел Dashboards/Manage и нажимаем кнопку «Import»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-22.PNG)

В открывшейся форме нажимаем кнопку «Upload JSON file»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-23.PNG)

Выбираем идущий в комплекте поставки пример отчета – файл Роботы-1627543691525.json – и нажимаем кнопку «Import»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-24.PNG)

Если все выполнено верно, и файл отчета корректный, сразу откроется сам отчет:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-25.PNG)

Далее публикуем его, чтобы получить внешнюю ссылку на этот отчет. Нажимаем на кнопку «Share dashboard or panel»:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-26.PNG)

В открывшейся форме ставим Shorten URL = true и копируем адрес ссылки:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-27.PNG)

Окончательная ссылка на отчет получается после ручной корректировки как
```
https://{IP Оркестратора}:44392/grafana/goto/zDhfKuZnz?orgId=1
```

## Добавление в конфигурационный файл WebApi ссылок на опубликованные отчеты

Ссылки на опубликованные отчеты добавляются в конфигурационный файл C:\Primo\WebApi\appsettings.ProdWin.json в секцию Grafana:ReportItems:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-28.PNG)

Задается Url отчета, полученный в разделе выше, и произвольное наименование отчета. После этого службу WebApi нужно перезапустить.

Проверить, что все настроено верно, можно через интерфейс Оркестратора в разделе Журнал/Отчеты:

![](../../../../orchestrator-new/resources/install/linux/additional-components-linux/grafana-29.PNG)

По клику по кнопке Robots («Robots» – наименование отчета из конфигурационного файла) откроется отчет в Grafana.
