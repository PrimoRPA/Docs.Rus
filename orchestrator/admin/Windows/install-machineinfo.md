# Установка MachineInfo как службы 
Раздел содержит инструкцию по установке MachineInfo как службы под Windows 2016 Server. В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена, поэтому есть возможность сразу установить MachineInfo. 

**Как установить MachineInfo:**

1. Распакуйте архив `C:\\**Install\\MachineInfo.zip` в `C:\\Primo\\MachineInfo`. Например, выполнив команды в PowerShell:
```
> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\MachineInfo.zip" -DestinationPath "C:\Primo\MachineInfo" -Force
```

2\. Создайте системную переменную окружения. Для этого в PoweShell выполните команду:
```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
Регистрируем Primo.Orchestrator. MachineInfo.exe как службу Windows и сразу запускаем её. Служба должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:
> $secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
> $mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\LOCAL SERVICE', $secpasswd)  
> New-Service -Name Primo.Orchestrator.MachineInfo -BinaryPathName "C:\Primo\MachineInfo\Primo.Orchestrator.MachineInfo.exe" -Credential $mycreds -Description "Primo.Orchestrator.MachineInfo" -DisplayName "Primo.Orchestrator.MachineInfo" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.MachineInfo"
> $s.Start()
```
:large_blue_circle: **Примечание:** пароль в `$secpasswd` можно указать любой.

После чего служба Primo.Orchestrator.MachineInfo будет отображаться в списке служб как запущенная:


![](<../../../.gitbook/assets/install-machineinfo-1.png>)

![](<../../../.gitbook/assets/nstall-machineinfo-2.png>)

3\. Откройте порт 5051 на файерволе.\
Если используется один сервер с MachineInfo, в конфигурационном файле службы WebApi нужно добавить на него ссылку:

![](<../../../.gitbook/assets/install-machineinfo-3.png>)

Параметр **Timeout** (по умолчанию 4 сек) – это время ответа, после которого сервис считается недоступным.

Если используется кластер MachineInfo, или MachineInfo используется в геокластере, в конфигурационном файле службы WebApi нужно прописать ссылки на все узлы кластера:

![](<../../../.gitbook/assets/install-machineinfo-4.png>)

Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. **Узлы нельзя скрывать за балансировщиком нагрузки!**
