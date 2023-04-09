# Установка RDP2
Раздел содержит инструкцию по установке RDP2 под Windows 2016 Server. 

**Как установить RDP2:**

1\. Распакуйте архив `C:\Install\RDP2.zip` в папку `C:\Primo\RDP2`.\
2\. Внесите изменения в конфигурационный файл RDP2 (`C:\Primo\RDP2\appsettings.ProdWin.json`):
* В секции **ConnectionStrings** измените **Host** для строки подключения к БД на реальный IP сервера БД.\
  Если поменялся пользователь/пароль БД – их тоже нужно отредактировать в этой секции. Пароль предварительно шифруем программой шифрования паролей:

![](<../../../.gitbook/assets/install-rdp2-1.png>)

3\. Проверьте, что значение системной переменной окружения **DOTNET_ENVIRONMENT** равно **ProdWin**. Для этого выполните в PoweShell команду:
```
> [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
```
:yellow_circle: ***Если системной переменной окружения DOTNET_ENVIRONMENT нет, создайте ее.*** Для этого выполните в PoweShell команду:
```
> [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
4\. Зарегистрируйте **Primo.Orchestrator.RDP2.exe** как службу Windows и сразу запустите ее. Для этого в PowerShell последовательно выполните команды:
```
> New-Service -Name Primo.Orchestrator.RDP2 -BinaryPathName "C:\Primo\RDP2\Primo.Orchestrator.RDP2.exe" -Description "Primo.Orchestrator.RDP2" -DisplayName "Primo.Orchestrator.RDP2" -StartupType Automatic 
```
5\. Запустите службу - она должна работать как локальная служба, то есть под **Local System account**:

![](<../../../.gitbook/assets/install-rdp2-2.png>)

Свойства службы:

![](<../../../.gitbook/assets/install-rdp2-3.png>)

6\. Проверьте, что RDP-сессия устанавливается корректно - для этого перейдите в UI Оркестратора:

![](<../../../.gitbook/assets/install-rdp2-4.png>)

7\. В Оркестраторе должны быть установлены следующие параметры сессии:

**Authentication Level = Attemp Authentication\
Negotiate Security Layer = True**

![](<../../../.gitbook/assets/install-rdp2-5.png>)

:white_check_mark: **Готово**: RDP2 успешно установлен под Windows 2016 Server.



