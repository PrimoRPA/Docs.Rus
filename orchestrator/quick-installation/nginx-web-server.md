# Установка Оркестратора на веб-сервер Nginx 

Конфигурация:
* Windows Server 2019
* Nginx
* PostgreSQL
* RabbitMQ

## Видеоинструкция

С видеоинструкцией по установке Оркестратора можно ознакомиться [здесь](https://www.youtube.com/watch?v=mOTH1PWxSCs).

[![Watch the video](<../../.gitbook/assets1/quick-install-nginx.gif>)](https://www.youtube.com/watch?v=mOTH1PWxSCs)


## Начальная подготовка 
> *Подробнее в «Руководстве по предварительной настройке машины Оркестратора под Windows 2016 Server.docx»*.

1. Переименуем сервер, дав ему простое и понятное название. Например, **ORCHESTRATOR**.
2. Раскомментируем в файле `C:\Windows\System32\drivers\etc\hosts` следующую строку:

![](<../../.gitbook/assets1/orch-install-nginxserver-1.png>)

3. Разрешаем удаленные подключения к хосту. Заходим в **Start Menu > Control Panel > System > Advanced System Settings > Remote** и включаем настройку, как на рисунке ниже:

![](<../../.gitbook/assets1/orch-install-nginxserver-2.png>)


## Шаг 1. Подготовка и установка дистрибутивов

> *Подробнее в «Руководстве по предварительной настройке машины Оркестратора под Windows 2016 Server.docx».*

1. Создаем папку `C:\Primo`.
2. Создаем папку `C:\Install` и копируем в нее нужные дистрибутивы:

![](<../../.gitbook/assets1/orch-install-nginxserver-3.png>)

3. Устанавливаем Google Chrome. Обновляем его до последней версии и делаем браузером по умолчанию.
4. Устанавливаем Notepad++. Все опции оставляем по умолчанию.
5. Устанавливаем PowerShell. При установке включаем все чекбоксы:

![](<../../.gitbook/assets1/orch-install-nginxserver-4.png>)

6. Создаем папку `docs` на рабочем столе и копируем туда следующую документацию из комплекта поставки:

![](<../../.gitbook/assets1/orch-install-nginxserver-18.png>)

## Шаг 2. Настройка PostgreSQL 

> *Подробнее в «Руководстве по установке PostgreSQL под Windows 2016 Server.docx»*.

Устанавливаем PostgreSQL Server:
1.	Распаковываем архив `postgresql-13.4-1-windows.zip` в папку `C:\Install`.
2.	Кликаем по файлу `C:\Install\postgresql-13.4-1-windows-x64.exe`.
3.	Выбираем **Да** в появившемся окне:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-5.png>)

4.	В следующем окне выбираем **Далее**.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-6.png>)

5.	Выбираем директорию (1), куда будет установлена программа. Оставляем все без изменения и жмем **Далее** (2).

   ![](<../../.gitbook/assets1/orch-install-nginxserver-7.png>)

6.	В окне выбора компонентов тоже все оставляем по умолчанию и нажимаем **Далее**.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-8.png>)

7.	Прописываем путь `C:\Primo\PostgreSQL\Data` (1), где будут располагаться файлы базы данных Оркестратора и конфигурационные файлы, нажимаем **Далее** (2).

   ![](<../../.gitbook/assets1/orch-install-nginxserver-9.png>)

8.	Вводим пароль\* (1) и его подтверждение (2) для суперпользователя БД (postgres), нажимаем **Далее**.

   > \**В дальнейшем пароль можно будет изменить в PostgreSQL.*

   ![](<../../.gitbook/assets1/orch-install-nginxserver-10.png>)

9.	В следующем окне не меняем настройки порта по умолчанию (`5432`) и нажимаем **Далее**.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-11.png>)

10.	Из выпадающего меню (1) выбираем **Русский, Россия** (2) и нажимаем **Далее** (3).

   ![](<../../.gitbook/assets1/orch-install-nginxserver-12.png>)

11.	Перепроверяем введенные данные (1). В случае необходимости можно вернуться, кликнув **Назад**, и исправить параметры. Если все верно, выбираем **Далее**.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-13.png>)

12. В следующем окне нажимаем **Далее**.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-14.png>)

13.	Дожидаемся завершения процесса установки.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-15.png>)

14.	Stack Builder не понадобится, убираем галочку (1) и нажимаем **Завершить** (2):

   ![](<../../.gitbook/assets1/orch-install-nginxserver-16.png>)

15. Заходим в PostgreSQL через pgAdmin (пользователь postgres/postgres). pgAdmin установится вместе с PostgreSQL и доступен через меню **Пуск**\**.

> \*\**Требуется для определения параметров оборудования. Если для этого используется сервис MachineInfo, то не нужно.*

15.1.	Создаем пользователя, под которым будут работать компоненты Оркестратора, и необходимые БД:

   ```
   CREATE ROLE orch_user WITH
     LOGIN
     NOSUPERUSER
     INHERIT
     NOCREATEDB
     NOCREATEROLE
     NOREPLICATION
     PASSWORD 'postgres';
   GRANT pg_execute_server_program TO orch_user;

   CREATE DATABASE ltools WITH OWNER orch_user;
   CREATE DATABASE ltoolslogs WITH OWNER orch_user;
   CREATE DATABASE ltoolsidentity WITH OWNER orch_user;
   CREATE DATABASE ltoolslicense WITH OWNER orch_user;
   ```

15.2.	В БД ltoolslicense выполняем скрипты из папки `C:\Install\ltoolslicense`:
   * get_cpu_id.sql;
   * get_hdd_id.sql;
   * get_host_name.sql.

:small_orange_diamond: ***ВАЖНО! При выполнении скриптов из postgresql-13/ltoolslicense нужно следить, чтобы случайно не внести изменения в текст скрипта. Недопустимо вносить даже незначимые, с точки зрения кода скрипта, пробелы и пустые строки. В том числе, если отредактировали скрипт в редакторе, который заменил визуально ненаблюдаемые символы конца строки (отличаются для Windows- и Linux-строк).***

16. Настраиваем доступ к БД по сети (по умолчанию она доступна только локально по localhost):
    * Открываем папку `C:\Primo\PostgreSQL\Data`.
    * Вносим изменения в файл `postgresql.conf`:
     ```
     listen_addresses = '*'
     ```
    * Вносим изменения в файл `pg_hba.conf`:
     ```
     local    all      all                  	trust
     host     all      all     0.0.0.0/0  	trust
     ```

    * Перезапускаем службу PostgreSQL.
    * Проверяем статус работы службы:

    ![](<../../.gitbook/assets1/orch-install-nginxserver-17.png>)

:white_check_mark: Установка и настройка сервера БД завершена.

## Шаг 3. Установка RabbitMQ 

> *Подробнее в «Руководстве по установке RabbitMQ под Windows 2016 Server.docx»*.

1. Разрешаем localhost в файле `C:\Windows\System32\drivers\etc\hosts`.  

![](<../../.gitbook/assets1/orch-install-nginxserver-between18and19.png>)

2. Разархивируем `rabbitmq.zip` в ту же папку `C:\Install\rabbitmq`.

3. Сначала устанавливаем Erlang (otp_win64_23.2.exe), все параметры оставляем по умолчанию.

4. Затем устанавливаем сам RabbitMQ (rabbitmq-server-3.8.11.exe), все параметры оставляем по умолчанию. 

5. Производим первоначальное конфигурирование RabbitMQ:

```
> cd C:\Program Files\RabbitMQ Server\rabbitmq_server-3.8.11\sbin
> rabbitmq-plugins.bat enable rabbitmq_management
> rabbitmqctl.bat add_user "admin" "Qwe123!@#" 
> rabbitmqctl.bat set_user_tags admin administrator 
> rabbitmqctl.bat set_permissions -p / admin ".*" ".*" ".*" 
> rabbitmqctl.bat stop
> rabbitmqctl.bat start_app
```

6. Открываем веб-интерфейс управления RabbitMQ на http://localhost:15672, убеждаемся, что он открывается:

![](<../../.gitbook/assets1/orch-install-nginxserver-19.png>)

Заходим под пользователем admin/Qwe123!@#.

![](<../../.gitbook/assets1/orch-install-nginxserver-20.png>)

Дальнейшее управление RabbitMQ можно осуществлять через этот веб-интерфейс.



## Шаг 4. Установка и запуск служб 

### MachineInfo 

> *Подробнее в «Руководстве по установке MachineInfo как службы под Windows 2016 Server.docx».*

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем MachineInfo. 

1. Разархивируем `C:\Install\MachineInfo.zip` в папку `C:\Primo\MachineInfo`. Можно при помощи команды в PowerShell:

```
> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\MachineInfo.zip" -DestinationPath "C:\Primo\MachineInfo" -Force
```

2. Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:

```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

3. Регистрируем `Primo.Orchestrator.MachineInfo.exe` как службу Windows и сразу запускаем её. Она должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:

```
> New-Service -Name Primo.Orchestrator.MachineInfo -BinaryPathName "C:\Primo\MachineInfo\Primo.Orchestrator.MachineInfo.exe" -Description "Primo.Orchestrator.MachineInfo" -DisplayName "Primo.Orchestrator.MachineInfo" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.MachineInfo"
> $s.Start()
```

4. После чего созданная служба Primo.Orchestrator.MachineInfo будет отображаться в списке всех служб как запущенная:

![](<../../.gitbook/assets1/orch-install-nginxserver-21.png>)

![](<../../.gitbook/assets1/orch-install-nginxserver-22.png>)

5. Открываем порт `5051` на файерволе.

6. Если используется один сервер с MachineInfo, в конфигурационном файле службы WebApi прописываем ссылку на него.

   Параметр **Timeout** (по умолчанию 4 сек.) – это время ответа, после которого сервис считается недоступным.

![](<../../.gitbook/assets1/orch-install-nginxserver-23.png>)

7. Если используется кластер MachineInfo, или MachineInfo используется в гео-кластере, в конфигурационном файле службы WebApi прописываются ссылки на все узлы кластера:

![](<../../.gitbook/assets1/orch-install-nginxserver-24.png>)

Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. Узлы нельзя скрывать за балансировщиком нагрузки (load balancer)!


### Notifications 

> *Подробнее в «Руководстве по установке Notifications под Windows 2016 Server.docx».*

1. Разархивируем `C:\Install\Notifications.zip` в папку `C:\Primo\Notifications`.

2. Редактируем конфигурацию Notifications в файле `C:\Primo\Notifications\appsettings.ProdWin.json`:
   * Правим секцию **Email**, отвечающую за SMTP-сервер, с которого будет происходить рассылка.

![](<../../.gitbook/assets1/orch-install-nginxserver-25.png>)

3. Проверяем, что значение системной переменной окружения DOTNET_ENVIRONMENT равно ProdWin. Для этого в PoweShell выполняем команду:

```
> [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
```
4. Если системная переменная окружения DOTNET_ENVIRONMENT не была создана, то создаем ее. Для этого в PowerShell выполняем команду:

```
> [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

5. Регистрируем `Primo.Orchestrator.Notifications.exe` как службу Windows и сразу запускаем её. Она должна работать как сетевая служба. Для этого в PoweShell последовательно выполняем команды:

```
> New-Service -Name Primo.Orchestrator.Notifications -BinaryPathName "C:\Primo\Notifications\Primo.Orchestrator.Notifications.exe" -Description "Primo.Orchestrator.Notifications" -DisplayName "Primo.Orchestrator.Notifications" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.Notifications"
> $s.Start()
```

6. После чего созданная служба **Primo.Orchestrator.Notifications** будет отображаться в списке всех служб как запущенная.

7. Через интерфейс Оркестратора переходим в раздел **Настройки > Пользователи**. Редактируем для пользователей параметры рассылки - указываем e-mail и типы событий:

![](<../../.gitbook/assets1/orch-install-nginxserver-26.png>)


### SecureSocketOption

Начиная с версии Оркестратора 1.24.6 в работу службы `LTools.Orchestrator.Notifications` добавлена возможность конфигурировать параметр `SecureSocketOption`  для почтовой рассылки.
 
#### Параметры `SecureSocketOption`

 - **`SecureSocketOptions.None (0)`**
  -  Не должно использоваться шифрование SSL или TLS.
  
 - **`SecureSocketOptions.Auto (4)`**
  -  Разрешает `MailKit.IMailService` выбирать, какие параметры SSL или TLS использовать (по умолчанию). Если сервер не поддерживает SSL или TLS, то соединение будет продолжаться без шифрования.

  - **`SecureSocketOptions.SslOnConnect (1)`**
  -  Соединение должно сразу использовать шифрование SSL или TLS.

 - **`SecureSocketOptions.StartTls (2)`**
  -  Повышает соединение до использования шифрования TLS сразу после чтения приветствия и возможностей сервера. Если сервер не поддерживает расширение STARTTLS, то соединение завершится с ошибкой и будет выброшено исключение `System.NotSupportedException`.

 - **`SecureSocketOptions.StartTlsWhenAvailable (3)`**
  -  Повышает соединение до использования шифрования TLS сразу после чтения приветствия и возможностей сервера, но только если сервер поддерживает расширение STARTTLS.

 Для настройки `SecureSocketOption` необходимо в конфигурационном файле в секции e-mail указать соответствующую цифру в зависимости от настроек почтового сервера.

```
{
  "Email": 
    "FromName": "Primo.RPA",
    "FromUserName": "mailing@primo-rpa.ru",
    "FromEmail": "mailing@primo-rpa.ru",
    "FromPassword": "CQZ0WKZkeJtyPyazHFc5yg==",
    "FromSmtp": "mail.primo-rpa.ru",
    "FromSmtpPort": 587,    
    "RequireAuthenticate": true,
    "SecureSocketOption": **1**
}
```

Обратите внимание, что если задан параметр **SecureSocketOption**, то параметр **UseSsl** будет игнорироваться.

### RDP2 

> *Подробнее в «Руководстве по установке RDP2 под Windows 2016 Server.docx»*.

1. Разархивируем `C:\Install\RDP2.zip` в папку`C:\Primo\RDP2`.

2. Редактируем конфигурацию RDP2 в файле `C:\Primo\RDP2\appsettings.ProdWin.json`:
   * Меняем в секции **Orchestrator** адрес Оркестратора и учетку пользователя, можно использовать только системного пользователя rdpservice:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-27.png>)

   * Если поменялся пароль пользователя **rdpservice** – меняем. Пароль предварительно шифруем программой шифрования паролей.
   * При необходимости устанавливаем значение **AddressFilter** для фильтрации по машине Агента либо оставляем поле пустым (будут использованы все Агенты системы).

3. Настраиваем путь до файла с логом и период ротации файла с логом (по умолчанию - день).

4. Проверяем, что значение системной переменной окружения DOTNET_ENVIRONMENT равно ProdWin. Для этого в PoweShell выполняем команду:

```
> [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
```

5. Создаем системную переменную окружения DOTNET_ENVIRONMENT, если она не создана ранее. Для этого в PowerShell выполняем команду:

```
> [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

6. Регистрируем `Primo.Orchestrator.RDP2.exe` как службу Windows и сразу запускаем её. Она должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:

```
> New-Service -Name Primo.Orchestrator.RDP2 -BinaryPathName "C:\Primo\RDP2\Primo.Orchestrator.RDP2.exe" -Description "Primo.Orchestrator.RDP2" -DisplayName "Primo.Orchestrator.RDP2" -StartupType Automatic
```

7. Запускаем службу. Служба должна работать под Local System account:

![](<../../.gitbook/assets1/orch-install-nginxserver-28.png>)

![](<../../.gitbook/assets1/orch-install-nginxserver-29.png>)

8. Переходим на вкладку **Восстановление** (Recovery) и проверяем, что действия при сбое установлены:

![](<../../.gitbook/assets1/orch-install-nginxserver-30.png>)

9. Проверяем через интерфейс Оркестратора, что RDP-сессия устанавливается корректно:

![](<../../.gitbook/assets1/orch-install-nginxserver-31.png>)

10. Параметры сессии должны быть установлены следующим образом:
* Authentication Level = Attemp Authentication
* Negotiate Security Layer = True

![](<../../.gitbook/assets1/orch-install-nginxserver-32.png>)


### RobotLogs 

> *Подробнее в «Руководстве по установке RobotLogs как службы под Windows 2016 Server.docx»*.

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем RobotLogs. 

1. Сначала требуется установить RabbitMQ (см. «Руководство по установке RabbitMQ под Windows 2016 Server.docx»). 
2. Разархивируем `C:\Install\RobotLogs.zip` в папку `C:\Primo\RobotLogs`. Можно при помощи команды в PowerShell:

```
> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\RobotLogs.zip" -DestinationPath "C:\Primo\RobotLogs " -Force
```

3. Создаем системную переменную окружения, если не создана ранее. Для этого в PoweShell выполняем команду:

```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

4. Настраиваем конфигурационный файл:
   * Настраиваем строки подключения в БД:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-33.png>)

   * Настраиваем **UserName** и **Password** сервера RabbitMQ, который используется для обработки логов со скринами рабочего стола:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-34.png>)

   * Настраиваем **Host**, **UserName** и **Password** сервера RabbitMQ, который используется для интеграции с Оркестратором:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-35.png>)

   * Открываем порт `5672` на файерволе сервера RabbitMQ, который используется для интеграции с Оркестратором. 

   * Сервер RabbitMQ, который используется для интеграции с Оркестратором, общий для очередей Primo.Orchestrator.RobotLogs и Primo.Orchestrator.WebApi. Поэтому требуется соблюдать соответствие названий очередей и обменников.

   * Настраиваем URL Оркестратора. При необходимости, можно поменять пароль встроенной системной записи Orchestrator – одновременно через UI Оркестратора и в этой секции конфига:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-36.png>)

   * Настраиваем **ScreenFilePath** – путь до файлов со скринами рабочего стола, которые собираются с машины робота. Папка по этому пути должна быть создана заранее, и на неё должны быть настроены права на чтение и запись для всех.

   ![](<../../.gitbook/assets1/orch-install-nginxserver-37.png>)

   * Настраиваем в соответствии с конфигурационным файлом WebApi список тенантов:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-38.png>)

5. Регистрируем `Primo.Orchestrator.RobotLogs.exe` как службу Windows и сразу запускаем её. Она должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:

```
> New-Service -Name Primo.Orchestrator.RobotLogs -BinaryPathName "C:\Primo\RobotLogs\Primo.Orchestrator.RobotLogs.exe" -Description "Primo.Orchestrator.RobotLogs" -DisplayName "Primo.Orchestrator.RobotLogs" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.RobotLogs"
> $s.Start()
```

6. После чего созданная служба **Primo.Orchestrator.RobotLogs** отобразится в списке всех служб как запущенная.

7. Открываем порт `56748` на файерволе, если служба RobotLogs не на одном сервере с Nginx для WebApi.

8. Проверяем, что в конфиге Nginx настроено проксирование на RobotLogs\*:

>\**Или аналогично настроено в IIS для узла UI, если используется IIS.*

![](<../../.gitbook/assets1/orch-install-nginxserver-39-1.png>)

![](<../../.gitbook/assets1/orch-install-nginxserver-39-2.png>)

9. В конфигурационном файле **Primo.Orchestrator.WebApi** переключаем прием логов на сервис RobotLogs и перезапускаем **Primo.Orchestrator.WebApi**:

![](<../../.gitbook/assets1/orch-install-nginxserver-40.png>)

10. Если запросы в RobotLogs проксируются через отдельный от WebApi эндпоинт, нужно указать в конфиг-файле **Primo.Orchestrator.WebApi** этот эндпоинт в RobotLogsBaseUrl:

![](<../../.gitbook/assets1/orch-install-nginxserver-41.png>)

В настоящее время не поддерживается. Зарезервирован для дальнейшей оптимизации приема логов от роботов.

Тонкая настройка производительности приема логов настраивается в секции **InputBufferRobotLogs**:

![](<../../.gitbook/assets1/orch-install-nginxserver-42.png>)

* **MaxQueueLength** – максимальный размер входного буфера приема логов от робота. Чем выше, тем больший размер пачек логов робот без потерь может слать в Оркестратор.
* **MaxBatchSize** – максимальный размер пачки за один раз сбрасываемый сервисом в БД ltoolslogs. Чем выше, тем меньше обращений в БД потребуется, но тем большее количество данных за один раз должно быть передано.
* **ThreadSleep** – время (мс) опроса входного буфера.


### States 

> *Подробнее в «Руководстве по установке States под Windows 2016 Server.docx»*.

1. Разархивируем `C:\Install\States.zip` в папку `C:\Primo\States`.

2. Редактируем конфигурационный файл States - `C:\Primo\States\appsettings.ProdWin.json`:
   * Находим секцию **ConnectionStrings**:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-43.png>)

   * И меняем значение **HOST** для всех строк подключения к БД на реальный IP серверов БД:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-44.png>)

   Если поменялся пользователь/пароль БД – их тоже меняем.

3. Проверяем, что значение системной переменной окружения DOTNET_ENVIRONMENT равно ProdWin. Для этого в PoweShell выполняем команду:

   ```
   > [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
   ```

   Создаем системную переменную окружения DOTNET_ENVIRONMENT, если она не создана ранее. Для этого в PowerShell выполняем команду:

   ```
   > [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
   ```

4. Регистрируем `Primo.Orchestrator.States.exe` как службу Windows и сразу запускаем. Она должна работать как сетевая служба. Для этого в PowerShell последовательно выполняем команды:

   ```
   > New-Service -Name Primo.Orchestrator.States -BinaryPathName "C:\Primo\States\Primo.Orchestrator.States.exe" -Description "Primo.Orchestrator.States" -DisplayName "Primo.Orchestrator.States " -StartupType Automatic 
   > $s = Get-Service "Primo.Orchestrator.States"
   > $s.Start()
   ```

После чего созданная служба **Primo.Orchestrator.States** будет отображаться в списке всех служб как запущенная.


### WebApi 

> *Подробнее в «Руководстве по установке WebApi как службы под Windows 2016 Server.docx»*.

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем WebApi. 

1. Разархивируем `C:\Install\WebApi.zip` в папку `C:\Primo\WebApi`. Можно при помощи команды в PowerShell:
   ```
   > Expand-Archive -LiteralPath "$InstallPath\WebApi.zip" -DestinationPath 'C:\Primo\WebApi' -Force
   ```
2. Редактируем конфигурацию WebApi в файле `C:\Primo\WebApi\appsettings.ProdWin.json`:
   * Меняем адрес на реальный IP вашего сервера. См. `nginx.config` и «Руководство по установке Nginx под Windows 2016 Server.docx».

   ![](<../../.gitbook/assets1/orch-install-nginxserver-45.png>)

3. Создаем папку для публикации дистрибутивов робота, например, `C:\tmp`, и указываем её в конфиге `appsettings.ProdWin.json`:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-46.png>)

4. Меняем в файле `appsettings.ProdWin.json` в секции **ConnectionStrings** значение **HOST** для всех строк подключения к БД на реальный IP серверов БД.

   Для PostgreSQL это секция:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-47.png>)

   Где меняем значение атрибута:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-49.png>)

   Для MS SQL SERVER меняем значение здесь:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-50.png>)

6. Если для работы лицензий используется сервис получения параметров оборудования, то настраиваем WebApi на работу с этим сервисом – вводим адрес сервиса:

![](<../../.gitbook/assets1/orch-install-nginxserver-51.png>)

7. Если поменялся пользователь/пароль БД – их тоже меняем.

8. Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
   ```
   > [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
   ```
9. Регистрируем `Primo.Orchestrator.WebApi.exe` как службу Windows и сразу запускаем. Она должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:
   ```
   > New-Service -Name Primo.Orchestrator.WebApi -BinaryPathName "C:\Primo\WebApi\Primo.Orchestrator.WebApi.exe" -Description "Primo.Orchestrator.WebApi" -DisplayName "Primo.Orchestrator.WebApi" -StartupType Automatic 
   > $s = Get-Service "Primo.Orchestrator.WebApi"
   > $s.Start()
   ```
10. После чего созданная служба **Primo.Orchestrator.WebApi** будет отображаться в списке всех служб как запущенная:

![](<../../.gitbook/assets1/orch-install-nginxserver-52.png>)

:small_orange_diamond: ***Служба может не запуститься.*** Наиболее вероятная причина – это неверный Connection string (пароль) в `appsettings.ProdWin.json`, или не развернута/не настроена какая-либо из четырех БД Оркестратора.

При обновлении службы WebApi может потребоваться дополнительная настройка для RabbitMQ. Для выполнения настройки необходимо перед стартом службы WebApi запустить скрипт из комплекта поставки: 
* `deletequeues.bat` – для RabbitMQ, запущенном на ОС Windows;
* `deletequeues.sh` – для RabbitMQ, запущеном на ОС Linux.

Скрипты необходимо запустить на сервере, на котором запущен RabbitMQ.

### Результат шага 4 

После того, как все перечисленные службы установлены, они должны появиться в диспетчере служб Windows:

![](<../../.gitbook/assets1/orch-install-nginxserver-53.png>)


## Шаг 5. Установка Nginx как службы Windows

> *Подробнее в «Руководстве по установке Nginx в качестве службы под Windows 2016 Server.docx»*.

Чтобы установить Nginx в качестве службы, необходимо:  

1.	Разархивировать файл `nginx-service.zip`, который идет в комплекте поставки, в папку `C:\Primo\nginx-1.21.1` (версия Nginx может измениться).

   ![](<../../.gitbook/assets1/orch-install-nginxserver-54.png>)

2.	Щелкнуть правой кнопкой мыши по пустому простанству и открыть PowerShell от имени администратора:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-55.png>)

3. Использовать команду установки:
   ```
   .\nginx-service.exe install
   ```

   ![](<../../.gitbook/assets1/orch-install-nginxserver-56.png>)

4.	После успешной установки службы запускать либо останавливать ее можно либо из **Управление сервером > Службы**:

   ![](<../../.gitbook/assets1/orch-install-nginxserver-57.png>)

   Либо из PowerShell (после установки службы окно PowerShell необходимо перезапустить) командами:

   ```
   > net stop nginx
   > net start nginx
   ```

   ![](<../../.gitbook/assets1/orch-install-nginxserver-58.png>)


### Установка UI на Nginx 

> *Подробнее в «Руководстве по установке UI на Nginx под Windows 2016 Server.docx»*.

Для варианта реализации Front на основе Nginx копируем содержимое папки UI из `C:\install\UI.zip` в `C:\Primo\nginx-1.21.1\html`.

**После этих шагов перезагружаем сервер.**


## Шаг 6. Проверка работы служб и Оркестратора

Заходим в список служб и проверяем, что все ранее установленные службы запущены:

![](<../../.gitbook/assets1/orch-install-nginxserver-59.png>)

Это службы:
-	nginx;
-	postgresql-x64-13;
-	Primo.Orchestrator.MachineInfo;
-	Primo.Orchestrator.Notifications;
-	Primo.Orchestrator.RDP2;
-	Primo.Orchestrator.RobotLogs;
-	Primo.Orchestrator.States;
-	Primo.Orchestrator.WebApi;
-	RabbitMQ.

Если какая-то из служб остановлена, то запускаем ее вручную.

Когда все службы запущены и работают, переходим по адресу: https://localhost:44392/

Логин: admin\
Пароль: Qwe123!@#

:white_check_mark: **На этом установка и базовая настройка завершены.**


