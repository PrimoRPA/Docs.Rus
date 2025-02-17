# Установка States под Windows 2016 Server

Разархивируйте C:\Install\States.zip в C:\Primo\States.

Отредактируйте конфигурационный файл States (C:\Primo\States\appsettings.ProdWin.json):

Поменяйте в секции RabbitMQ конфигурационного файла appsettings.ProdWin.json параметры для подключения к RabbitMQ:

![](../../../orchestrator-new/resources/install/windows/states-1.PNG)

Проверьте, что значение системной переменной окружения ASPNETCORE_ENVIRONMENT равно ProdWin. Для этого в PoweShell выполните команду:
```
[Environment]::GetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'Machine')
```
Создайте системную переменную окружения ASPNETCORE_ENVIRONMENT, если она не создана ранее. Для этого в PowerShell выполните команду:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Зарегистрируйте Primo.Orchestrator.States.exe как службу Windows и сразу запустите её. 

Служба должна работать как сетевая служба. Для этого в PowerShell последовательно выполните команды:
```
New-Service -Name Primo.Orchestrator.States -BinaryPathName "C:\Primo\States\Primo.Orchestrator.States.exe" -Description "Primo.Orchestrator.States" -DisplayName "Primo.Orchestrator.States " -StartupType Automatic 
$s = Get-Service "Primo.Orchestrator.States"
$s.Start()
```
После чего созданная служба Primo.Orchestrator.States будет отображаться в списке всех служб как запущенная.
