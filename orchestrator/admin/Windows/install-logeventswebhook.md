# Руководство по установке LogEventsWebhook как службы под Windows 2016 Server
Раздел содержит инструкцию по установке LogEventsWebhook как службы под Windows 2016 Server.

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем WebApi. 
Разархивируем C:\Install\LogEventsWebhook.zip в C:\Primo\LogEventsWebhook. Можно при помощи PowerShell:

> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\LogEventsWebhook.zip" -DestinationPath "C:\Primo\LogEventsWebhook" -Force

Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
Настраиваем appsettings.ProdWin.json (некоторые параметры):
