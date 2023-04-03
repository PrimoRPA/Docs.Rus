# Установка MachineInfo как службы 
Раздел содержит инструкцию по установке MachineInfo как службы под Windows 2016 Server.

В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена. Поэтому сразу устанавливаем MachineInfo. 
Разархивируем C:\Install\MachineInfo.zip в C:\Primo\MachineInfo. Можно при помощи PowerShell:

> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\MachineInfo.zip" -DestinationPath "C:\Primo\MachineInfo" -Force

Создаем системную переменную окружения. Для этого в PoweShell выполняем команду:
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
Регистрируем Primo.Orchestrator. MachineInfo.exe как службу Windows и сразу запускаем её. Служба должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:
> $secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
> $mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\LOCAL SERVICE', $secpasswd)  
> New-Service -Name Primo.Orchestrator.MachineInfo -BinaryPathName "C:\Primo\MachineInfo\Primo.Orchestrator.MachineInfo.exe" -Credential $mycreds -Description "Primo.Orchestrator.MachineInfo" -DisplayName "Primo.Orchestrator.MachineInfo" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.MachineInfo"
> $s.Start()
После чего созданная служба Primo.Orchestrator.MachineInfo будет отображаться в списке всех служб как запущенная:


![](<../../../.gitbook/assets/install-arcsight-1.png>)

![](<../../../.gitbook/assets/install-arcsight-1.png>)

Открываем порт 5051 на файерволе.
	Если используется один сервер с MachineInfo, в конфигурационном файле службы WebApi прописывается ссылка на него:

![](<../../../.gitbook/assets/install-arcsight-1.png>)

Timeout (по умолчанию 4 сек) – время ответа, после которого сервис считается не доступным.
Если используется кластер MachineInfo, или MachineInfo используется в гео-кластере, в конфигурационном файле службы WebApi прописываются ссылки на все узлы кластера:

![](<../../../.gitbook/assets/install-arcsight-1.png>)

Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. Узлы нельзя скрывать за лоадбалансером!
