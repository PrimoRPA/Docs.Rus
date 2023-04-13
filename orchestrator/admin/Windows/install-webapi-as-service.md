# Установка WebApi как службы

Раздел содержит инструкцию по установке WebApi как службы в Windows 2016 Server. Поскольку в Windows 2016 Server среда исполнения ASP .NET Core предустановлена, мы сразу можем переходить к установке WebApi. 

**Последовательно выполняем шаги:**

1\. Разархивируем `C:\Install\WebApi.zip` в `C:\Primo\WebApi`. Можно при помощи PowerShell:
```
> Expand-Archive -LiteralPath "$InstallPath\WebApi.zip" -DestinationPath 'C:\Primo\WebApi' -Force
```
2\. Редактируем конфиг WebApi (`C:\Primo\WebApi\appsettings.ProdWin.json`):
*Меняем на реальный (который у вашего сервера, см. nginx.config «Руководство по установке Nginx под Windows 2016 Server.docx») IP:

![](<../../../.gitbook/assets/>)

3\. Создаем папку для публикации дистрибутивов Робота, например, `C:\tmp`, и указываем её в конфиге `appsettings.ProdWin.json`:

![](<../../../.gitbook/assets/>)

Меняем в секции ConnectionStrings конфига appsettings.ProdWin.json HOST для всех строк подключения к БД на реальный IP серверов БД:
Тут (для PostgreSQL):

![](<../../../.gitbook/assets/>)

или тут (для MS SQL SERVER):

![](<../../../.gitbook/assets/>)
 
меняем это:

![](<../../../.gitbook/assets/>)
 
или это:
 
![](<../../../.gitbook/assets/>)

Если для работы лицензий используется сервис получения параметров оборудования, то настраиваем WebApi на работу с этим сервисом – вводим адрес этого сервиса:

![](<../../../.gitbook/assets/>)
 
Если поменялся пользователь/пароль БД – их тоже меняем.

Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

Регистрируем Primo.Orchestrator.WebApi.exe как службу Windows и сразу запускаем её. Служба должна работать как сетевая служба. Для этого в PowerShell последовательно выполняем команды:
```
> $secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
> $mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\NETWORK SERVICE', $secpasswd)  
> New-Service -Name Primo.Orchestrator.WebApi -BinaryPathName "C:\Primo\WebApi\Primo.Orchestrator.WebApi.exe" -Credential $mycreds -Description "Primo.Orchestrator.WebApi" -DisplayName "Primo.Orchestrator.WebApi" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.WebApi"
> $s.Start()
```
После чего созданная служба Primo.Orchestrator.WebApi будет отображаться в списке всех служб как запущенная:

![](<../../../.gitbook/assets/>)
 
Служба может не запуститься. Наиболее вероятная причина – это не верный коннекшнстринг (пароль) в appsettings.ProdWin.json и/или не развернута/не настроена какая-либо из 4-х БД Оркестратора.

При обновлении службы WebApi может потребоваться дополнительная настройка для RabbitMQ. Для выполнения настройки необходимо перед стартом службы WebApi запустить скрипт из комплекта поставки: deletequeues.bat – для RabbitMQ, запущенном на ОС Windows и deletequeues.sh – для RabbitMQ, запущеном на ОС Linux. Скрипты необходимо запустить на сервере, на котором запущен RabbitMQ. 

:white_check_mark: **Готово**: WebApi как служба успешно установлена в Windows 2016 Server и готова к работе.



