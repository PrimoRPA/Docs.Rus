# Установка TimescaleDB
Раздел содержит инструкцию по установке **TimescaleDB* под Windows 2016 Server. 

Расширение для базы данных PostgreSQL  12 – TimescaleDB – используется в Оркестраторе для Logs DB (см. Введение, рисунок 1).

**Как установить TimescaleDB:**

1\. Проверяем, что в системной переменной окружения Path установлен путь, соответствующей версии PostgreSQL:

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

Если он отсутствует, добавляем его вручную.

2\. Распакуем архив `C:\Install\timescaledb-postgresql-12_1.7.4-windows-amd64.zip` в папку `C:\Install`.\
3\. Внесите изменения в конфигурационный файл States (`C:\Primo\States\appsettings.ProdWin.json`):
* В секции **ConnectionStrings** измените **HOST** для всех строк подключения к БД на реальный IP серверов БД.\
  Если поменялся пользователь/пароль БД – их тоже нужно изменить.

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

3\. Проверьте, что значение системной переменной окружения **DOTNET_ENVIRONMENT** равно **ProdWin**. Для этого выполните в PoweShell команду:
```
> [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
```
:yellow_circle: ***Если переменная DOTNET_ENVIRONMENT не была создана ранее, создайте ее***. Для этого в PowerShell выполните команду:
```
> [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
4\. Зарегистрируйте `Primo.Orchestrator.States.exe` как службу Windows и сразу запустите её. Она должна работать как сетевая служба.

Для этого в PowerShell последовательно выполните команды:
```
> $secpasswd = ConvertTo-SecureString 'Qwe123!@#' -AsPlainText -Force 
> $mycreds = New-Object System.Management.Automation.PSCredential ('NT AUTHORITY\NETWORK SERVICE', $secpasswd)  
> New-Service -Name Primo.Orchestrator.States -BinaryPathName "C:\Primo\States\Primo.Orchestrator.States.exe" -Credential $mycreds -Description "Primo.Orchestrator.States" -DisplayName "Primo.Orchestrator.States " -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.States"
> $s.Start()
```
:white_check_mark: **Готово**: создана сетевая служба **Primo.Orchestrator.States**, которая будет отображаться в списке всех служб как запущенная.
