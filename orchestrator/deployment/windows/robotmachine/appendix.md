# Установка агента без инсталлятора
Раздел предназначен для опытных пользователей и содержит инструкцию для тонкой настройки машины Робота. 

## Установка PowerShell Core
Производится в соответствии с инструкцией «Руководство по установке PowerShell-7.1.3 под Windows.docx» из комплекта поставки.

## Установка агента Оркестратора
Создаем переменную окружения из PowerShell:
```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Проверить настройку переменных можно через System Properties/Advanced ➝ Environment Variables:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-1.png>)

![](<../../../../.gitbook/assets/robot-machine-without-istaller-2.png>)

Копируем файлы из дистрибутива Агента через PowerShell:
```
>$InstallPath = "C:\Install" 
>Expand-Archive -LiteralPath "$InstallPath\Agent.zip" -DestinationPath 'C:\Primo\Agent'
```
Проверяем, что файлы скопировались в папку C:\Primo\Agent:
  
![](<../../../../.gitbook/assets/robot-machine-without-istaller-3.png>)

Создаем службу из PowerShell:
```
>New-Service -Name "Primo.Orchestrator.Agent" -BinaryPathName "C:\Primo\Agent\Primo.Orchestrator.Agent.exe" -Description "Primo.Orchestrator.Agent" -DisplayName "Primo.Orchestrator.Agent" -StartupType Automatic
```

![](<../../../../.gitbook/assets/robot-machine-without-istaller-4.png>)

Редактируем конфигурационный файл `C:\Primo\Agent\appsettings.ProdWin.json` – указываем IP-адрес Оркестратора, TenantId Агента и пользователя из тенанта. Для дефолтного тенанта null.

```json

```

Запускаем службу:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-5.png>)

Служба должна работать под Local System account:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-6.png>)

## Настройка брандмауэра Windows
Открываем порты для http-сервера Агента (5002) и Роботов (8000-9000) – по этим портам к ним обращается сервер Оркестратора.
В PowerSchell выполняем команды:
```
>New-NetFirewallRule -Name "Primo Agent (5002)" -DisplayName "Primo Agent (5002)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 5002

>New-NetFirewallRule -Name "Primo Robot (8000-9000)" -DisplayName "Primo Robot (8000-9000)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 8000-9000
```

## Проверка настройки машины Робота
Проверяем, что сервис Агента (Primo.Agent) запущен.

Проверяем доступность машины Оркестратора с машины Робота. В браузере на машине Робота вводим адрес (см. п. 3.4):
```
https://<IP-адрес-машины-Оркестратора>:44392/login
```
и убеждаемся, что откроется страница авторизации:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-7.png>)


## Удержание RDP-сессий 
Возможно настроить машину Робота для 2-х альтернативных способов удержания RDP-сессий (требуется для работы Робота с рабочим столом):  

![](<../../../../.gitbook/assets/robot-machine-without-istaller-8.png>)

### Удержание одной RDP-сессии в консоли
Для этого нужно файл `restore_console.bat` из комплекта поставки разместить в корне диска C:\. Закрывать RDP-сессию необходимо при помощи запуска этого файла из cmd. Для автоматизации этого запуска, чтобы он проводился автоматически при отключении пользователя от сессии, можно создать Windows Task на событие «On disconnect on user session».

На основе импорта из файла RDP-Disconnector.xml нужно создать Windows Task:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-9.png>)

Проверяем свойства создаваемой Windows Task «RDP-Disconnector»:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-10.png>)

Windows Task «RDP-Disconnector» должна работать под локальным администратором:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-11.png>)

Проверяем наличие созданной Windows Task «RDP-Disconnector»:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-12.png>)

### Удержание многих RDP-сессий за счет внешних RDP-подключений

Для этого используется дополнительный сервис. 

Заводятся пользователи для RDP-сессий, например, user1 и user2: 

![](<../../../../.gitbook/assets/robot-machine-without-istaller-13.png>)

Пользователи желательно должны входить в группу Administrators:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-14.png>)

Если пользователи не входят в группу Administrators, то обязательно (!) должны входить в группы Users и Remote Desktop Users.
Добавленные пользователи должны быть зарегистрированы для машины робота (имя пользователя/пароль, и т.д.) в Оркестраторе:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-15.png>)

В Оркестраторе для RDP-пользователя должны быть настроены параметры безопасности подключения:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-16.png>)

Параметры RDP-подключения:
1. AuthenticationLevel  – 1 
2. NegotiateSecurityLayer  – true
3. EnableCredSspSupport  – true
4. DesktopWidth – Разрешение экрана по ширине (1920).
5. DesktopHeight – Разрешение экрана по высоте (880).
6. ColorDepth – Цветопередача (32).

К машине робота должны быть разрешены RDP-подключения:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-17.png>)

должны быть настроены параметры подключения, открыт порт для RDP:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-18.png>)

Если используется сервер удаленных рабочих столов, то необходимо его настроить. Запустить оснастку gpedit.msc (Win+R, рисунок 33) :

![](<../../../../.gitbook/assets/robot-machine-without-istaller-19.png>)

На вкладке Security:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-20.png>)

На вкладке Connections:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-21.png>)

Блокировка экрана пользователя должна быть отключена. Локально, или через групповые политики AD:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-22.png>)

Сервис RDP-подключений запускается на внешней машине, например, на машине с WebApi. На одну сессию сервис расходует порядка 100 Мб памяти.
RDP-сессии запускаются автоматически при старте роботов. Этот процесс требует некоторого времени, в течении которого робот должен подождать открытия. Эти параметры задаются в конфиге WebApi:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-23.png>)

Продолжительность ожидания запуска RDP-сессию:

![](<../../../../.gitbook/assets/robot-machine-without-istaller-24.png>)

## Настройка машины Робота из скрипта

Настройку машины Робота можно выполнить посредством PowerShell-скрипта PrimoWorker.ps1, который входит в комплект поставки Оркестратора. 

В скрипте нужно установить значения переменных в секции Input. Все необходимые комментарии содержатся в самом скрипте.

![](<../../../../.gitbook/assets/robot-machine-without-istaller-25.png>)

Разрешим выполнение неподписанного скрипта, выполнив перед его запуском в PowerShell-команду:
```
>Set-ExecutionPolicy Bypass -Scope Process -Force
```
Запускаем скрипт PrimoWorker.ps1 и дожидаемся окончания его выполнения. Проверяем настройку машины робота (см. п.5).




