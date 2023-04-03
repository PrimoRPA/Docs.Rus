# Установка ArcSight как службы

Раздел содержит инструкцию по установке ArcSight как службы под Windows 2016 Server.

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем ArcSight. 
Разархивируем C:\Install\ArcSight.zip в C:\Primo\ArcSight. Можно при помощи PowerShell:

> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\ArcSight.zip" -DestinationPath "C:\Primo\ArcSight " -Force

Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
Настраиваем уровни логирования приложения (Information, Warning, Error):
