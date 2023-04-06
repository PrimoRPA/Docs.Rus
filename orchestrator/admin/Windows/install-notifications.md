# Установка Notifications под Windows 2016 Server
Раздел содержит инструкцию по установке Notifications под Windows 2016 Server.

**Как установить Notifications:**

1\. Распакуйте архив `C:\Install\Notifications.zip в C:\Primo\Notifications`.\
2\. Внесите изменения в конфигурационный файл Notifications (`C:\Primo\Notifications\appsettings.ProdWin.json`), а именно:
    
  * отредактируйте секцию **Email** - она отвечает за SMTP-сервер, с которого будет происходить рассылка.

![](<../../../.gitbook/assets/install-notifications-1.png>)

3\. Проверьте, что значение системной переменной окружения DOTNET_ENVIRONMENT равно `ProdWin`. Для этого в PoweShell выполните команду:
```
> [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
```
:yellow_circle: **Если системная переменная окружения DOTNET_ENVIRONMENT не существует, создайте ее через PoweShell с помощью команды:**
```
> [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
4\. Зарегистрируйте **Primo.Orchestrator.Notifications.exe** как службу Windows и сразу запустите. Она должна работать как сетевая служба. Для этого в PoweShell последовательно выполните команды:
```
> $secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
> $mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\NETWORK SERVICE', $secpasswd)  
> New-Service -Name Primo.Orchestrator.Notifications -BinaryPathName "C:\Primo\Notifications\Primo.Orchestrator.Notifications.exe" -Credential $mycreds -Description "Primo.Orchestrator.Notifications" -DisplayName "Primo.Orchestrator.Notifications" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.Notifications"
> $s.Start()
```
:large_blue_circle: **Примечание:** пароль в `$secpasswd` можно задать любой. 

После чего созданная служба Primo.Orchestrator.Notifications будет отображаться в списке служб как запущенная.

5\. Перейдите в UI Оркестратора и в разделе **Настройки ➝ Пользователи** отредактируйте для пользователей параметры рассылки: укажите e-mail и типы событий, по которым необходимо получать уведомления:

![](<../../../.gitbook/assets/install-notifications-2.png>)

:white_check_mark: **Готово**: уведомления успешно настроены.
