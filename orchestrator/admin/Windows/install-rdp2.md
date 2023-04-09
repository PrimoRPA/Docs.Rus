# Установка RDP2
Раздел содержит инструкцию по установке RDP2 под Windows 2016 Server. 

**Как установить RDP2:**

1\. Распакуйте архив `C:\Install\RDP2.zip` в папку `C:\Primo\RDP2`.
2\. Внесите изменения в конфигурационный файл RDP2 (`C:\Primo\RDP2\appsettings.ProdWin.json`):
* В секции **ConnectionStrings** измените **Host** для строки подключения к БД на реальный IP сервера БД.\
  Если поменялся пользователь/пароль* БД – их тоже нужно отредактировать в этой секции. Пароль предварительно шифруем программой шифрования паролей.

![](<../../../.gitbook/assets/install-rdp2-1.png>)

3\. Проверьте, что значение системной переменной окружения **DOTNET_ENVIRONMENT** равно **ProdWin**. Для этого выполните команду в PoweShell:
```
> [Environment]::GetEnvironmentVariable('DOTNET_ENVIRONMENT', 'Machine')
```
Создаем системную переменную окружения DOTNET_ENVIRONMENT, если она не создана ранее. Для этого в PowerShell выполняем команду:
```
> [System.Environment]::SetEnvironmentVariable('DOTNET_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Регистрируем Primo.Orchestrator.RDP2.exe как службу Windows и сразу запускаем её. Служба должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:
```
> New-Service -Name Primo.Orchestrator.RDP2 -BinaryPathName "C:\Primo\RDP2\Primo.Orchestrator.RDP2.exe" -Description "Primo.Orchestrator.RDP2" -DisplayName "Primo.Orchestrator.RDP2" -StartupType Automatic 
```
Запускаем службу. Служба должна работать под Local System account:

![](<../../../.gitbook/assets/install-rdp2-2.png>)

![](<../../../.gitbook/assets/install-rdp2-3.png>)

Проверяем, что RDP-сессия устанавливается корректно:

![](<../../../.gitbook/assets/install-rdp2-4.png>)

Параметры сессии должны быть установлены:
```
Authentication Level = Attemp Authentication
Negotiate Security Layer = True
```

![](<../../../.gitbook/assets/install-rdp2-5.png>)

:white_check_mark: **Готово**: RDP2 успешно установлен под Windows 2016 Server.



