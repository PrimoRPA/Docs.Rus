# Установка LogEventsWebhook как службы
Раздел содержит инструкцию по установке LogEventsWebhook как службы под Windows 2016 Server. В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена, поэтому возможно сразу установить WebApi. 

Как это сделать:

1. Разархивируйте C:\\**Install\LogEventsWebhook.zip** в C:\\**Primo\LogEventsWebhook** при помощи PowerShell:
```
$InstallPath = "C:\Install"
Expand-Archive -LiteralPath "$InstallPath\LogEventsWebhook.zip" -DestinationPath "C:\Primo\LogEventsWebhook" -Force
```

2\. Создайте системную переменную окружения. Для этого в PoweShell выполните команду:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```

3\. Настройте параметры в файле appsettings.ProdWin.json:

![](<../../../.gitbook/assets/install-webhooks-1.png>)

**Описание необходимых параметров:**

* В секции RabbitMQ задайте параметр **Host** – адрес сервера с RabbitMQ.
* В секции HttpEndPoint полностью укажите все параметры:
  * **Url** – адрес end-point приема событий.
  * **LoginUrl** – адрес end-point получения токена.
  * **UserName** – имя пользователя для получения токена.
  * **Password** – пароль для получения токена. Пароль должен быть зашифрован утилитой LTools.Orchestrator.PasswordEncriptor.
* В секции Orchestrator задайте параметр **BaseUrl** – адрес Оркестратора.
* В секции Cache настройте атрибут параметра **EntityData**:
  * **DurationInMinutes** – время (минут) жизни кэша для получения расширенной информации о связанной с событием сущности Оркестратора.

4\. Настройте уровни логирования (Information, Warning, Error):

![](<../../../.gitbook/assets/install-webhooks-2.png>)

5\. Настройте путь до папки с логами и шаблон имени файлов логов:

![](<../../../.gitbook/assets/install-webhooks-3.png>)

5\. Зарегистрируйте Primo.Orchestrator.LogEventsWebhook.exe как службу Windows и сразу запустите. Она должна работать как локальная служба. Для этого последовательно выполните в PowerShell команды:
```
$secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
$mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\LOCAL SERVICE', $secpasswd)  
New-Service -Name Primo.Orchestrator.LogEventsWebhook -BinaryPathName "C:\Primo\LogEventsWebhook\Primo.Orchestrator.LogEventsWebhook.exe" -Credential $mycreds -Description "Primo.Orchestrator.LogEventsWebhook" -DisplayName "Primo.Orchestrator.LogEventsWebhook" -StartupType Automatic 
$s = Get-Service "Primo.Orchestrator.LogEventsWebhook"
$s.Start()
```
**Примечание к коду**: в `$secpasswd` можно задать любой пароль.

После чего служба Primo.Orchestrator.LogEventsWebhook будет отображаться в списке служб как запущенная:

![](<../../../.gitbook/assets/install-webhooks-4.png>)

![](<../../../.gitbook/assets/install-webhooks-5.png>)

6\. В завершение в конфигурационном файле службы WebApi нужно разрешить интеграцию:

![](<../../../.gitbook/assets/install-webhooks-6.png>)
