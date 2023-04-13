# Установка WebApi как службы

Раздел содержит инструкцию по установке **WebApi как службы** в Windows 2016 Server. Поскольку в Windows 2016 Server среда исполнения ASP .NET Core предустановлена, мы сразу можем переходить к установке WebApi. 

**Последовательно выполняем шаги:**

1\. Распакуем архив `C:\Install\WebApi.zip` в папку `C:\Primo\WebApi`. Можно воспользоваться PowerShell:
```
> Expand-Archive -LiteralPath "$InstallPath\WebApi.zip" -DestinationPath 'C:\Primo\WebApi' -Force
```
2\. Внесем изменения в конфигурационный файл WebApi (`C:\Primo\WebApi\appsettings.ProdWin.json`):
* В секции `RobotDeployment` меняем значение параметра `OrchBaseUrl` на реальный IP (который у вашего сервера, см. nginx.config «Руководство по установке Nginx под Windows 2016 Server.docx»):

![](<../../../.gitbook/assets/install-webapi-as-service-1.png>)

* Создаем папку для публикации дистрибутивов Робота, например, `C:\tmp` и указываем её в конфигурационном файле в секции `RobotDistrUpload`:

![](<../../../.gitbook/assets/install-webapi-as-service-2.png>)

* В секции `ConnectionStrings` конфигурационного файла `appsettings.ProdWin.json` меняем **HOST** для всех строк подключения к БД на реальный IP серверов БД.
  * Для **PostgreSQL** меняем подчеркнутые значения:

![](<../../../.gitbook/assets/install-webapi-as-service-3.png>)

  * Для **MS SQL SERVER** меняем подчеркнутые значения:

![](<../../../.gitbook/assets/install-webapi-as-service-4.png>)

* Если для работы лицензий используется сервис получения параметров оборудования, то настраиваем WebApi на работу с этим сервисом – вводим адрес этого сервиса в секции `License`:

![](<../../../.gitbook/assets/install-webapi-as-service-5.png>)
 
* Если поменялся пользователь/пароль БД – их тоже изменяем.

3\. Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

4\. Регистрируем `Primo.Orchestrator.WebApi.exe` как службу Windows и сразу запускаем её. Она должна работать как сетевая служба. Для этого в PowerShell последовательно выполняем команды:
```
> $secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
> $mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\NETWORK SERVICE', $secpasswd)  
> New-Service -Name Primo.Orchestrator.WebApi -BinaryPathName "C:\Primo\WebApi\Primo.Orchestrator.WebApi.exe" -Credential $mycreds -Description "Primo.Orchestrator.WebApi" -DisplayName "Primo.Orchestrator.WebApi" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.WebApi"
> $s.Start()
```
:grey_exclamation: *Пароль в `$secpasswd` можно задать любой*

После этого созданная служба **Primo.Orchestrator.WebApi** будет отображаться в списке всех служб как запущенная:

![](<../../../.gitbook/assets/install-webapi-as-service-6.png>)
 
:bangbang: Служба может не запуститься. Наиболее вероятная причина – это неверный connection string (пароль) в `appsettings.ProdWin.json` и/или не развернута/не настроена какая-либо из 4-х БД Оркестратора.

При обновлении службы WebApi может потребоваться дополнительная настройка для RabbitMQ. Для выполнения настройки необходимо перед стартом службы WebApi запустить скрипт из комплекта поставки: 
* `deletequeues.bat` – для RabbitMQ, запущенном на ОС Windows; 
* `deletequeues.sh` – для RabbitMQ, запущеном на ОС Linux. 
 
Скрипты необходимо запустить на сервере, на котором запущен RabbitMQ. 
