# Руководство по установке LogEventsWebhook как службы под Windows 2016 Server
Раздел содержит инструкцию по установке LogEventsWebhook как службы под Windows 2016 Server.

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем WebApi. 
Разархивируем C:\Install\LogEventsWebhook.zip в C:\Primo\LogEventsWebhook. Можно при помощи PowerShell:

> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\LogEventsWebhook.zip" -DestinationPath "C:\Primo\LogEventsWebhook" -Force

Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
Настраиваем appsettings.ProdWin.json (некоторые параметры):

![](<../../../.gitbook/assets/install-webhooks-1.png>)

![](<../../../.gitbook/assets/install-webhooks-2.png>)

![](<../../../.gitbook/assets/install-webhooks-3.png>)

![](<../../../.gitbook/assets/install-webhooks-4.png>)

![](<../../../.gitbook/assets/install-webhooks-5.png>)

![](<../../../.gitbook/assets/install-webhooks-6.png>)
