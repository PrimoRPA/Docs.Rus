# Установка Агента без инсталлятора
Раздел предназначен для опытных пользователей и содержит инструкцию для тонкой настройки машины робота. 

## Установка PowerShell Core
Производится в соответствии с инструкцией [Установка PowerShell-7.1.3 под Windows](../../../../orchestrator-new/install/windows/setting-up-machines-win/install-powershell.md).

## Установка агента Оркестратора
Создаем переменную окружения из PowerShell:
```
[System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
Проверить настройку переменных можно через **System Properties ➝ Advanced** по кнопке **Environment Variables**:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-1.PNG>)

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-2.PNG>)

Копируем файлы из дистрибутива Агента через PowerShell:
```
$InstallPath = "C:\Install" 
Expand-Archive -LiteralPath "$InstallPath\Agent.zip" -DestinationPath 'C:\Primo\Agent'
```
Проверяем, что файлы скопировались в папку `C:\Primo\Agent`:
  
![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-3.PNG>)

Создаем службу из PowerShell:
```
New-Service -Name "Primo.Orchestrator.Agent" -BinaryPathName "C:\Primo\Agent\Primo.Orchestrator.Agent.exe" -Description "Primo.Orchestrator.Agent" -DisplayName "Primo.Orchestrator.Agent" -StartupType Automatic
```
Отображение службы Primo.Orchestrator.Agent среди всех служб:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-4.PNG>)

Редактируем конфигурационный файл `C:\Primo\Agent\appsettings.ProdWin.json` – указываем IP-адрес Оркестратора, TenantId Агента и пользователя из тенанта\*. Для дефолтного тенанта null.

\* *Встроенная учетная запись agent из тенанта по умолчанию. Для шифрования пароля используется программа шифрования паролей PasswordEncryptor.zip из комплекта поставки Оркестратора.*

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-5.PNG>)

Запускаем службу:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-6.PNG>)

Служба должна работать под Local System account:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-7.PNG>)

## Настройка брандмауэра Windows
Открываем [порты](../orchestrator-new/ports.md) для HTTP-сервера Агента (5002) и роботов (8000-9000) – по этим портам к ним обращается сервер Оркестратора.

В PowerShell выполняем команды:
```
New-NetFirewallRule -Name "Primo Agent (5002)" -DisplayName "Primo Agent (5002)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 5002

New-NetFirewallRule -Name "Primo Robot (8000-9000)" -DisplayName "Primo Robot (8000-9000)" -Profile "Private, Domain, Public" -Direction Inbound -Action Allow -Protocol TCP -LocalPort 8000-9000
```

## Проверка настройки машины робота
Проверяем, что сервис Агента (Primo.Agent) запущен - для этого просматриваем статус службы в **Services**.

Проверяем доступность машины Оркестратора с машины робота. В браузере на машине робота вводим адрес:
```
https://<IP-адрес-машины-Оркестратора>:44392/login
```
и убеждаемся, что открывается страница авторизации:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-8.PNG>)

Проверяем, что работают (если не выключены в конфигурационном файле, секция Performance, параметр Enabled) метрики производительности на главной странице:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-9.PNG>)

и в логе нет связанных с ними ошибок. Если в логе есть ошибка счетчиков производительности Windows, сходная с представленной ниже:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-9(2).PNG>)

нужно настроить работу счетчиков средствами ОС: 

* [Перестроение значений библиотеки счетчиков производительности вручную](https://learn.microsoft.com/ru-ru/troubleshoot/windows-server/performance/rebuild-performance-counter-library-values)

* [Manually rebuild performance counter library values](https://learn.microsoft.com/en-us/troubleshoot/windows-server/performance/rebuild-performance-counter-library-values)


## Удержание RDP-сессий 
Возможно настроить машину робота для 2-х альтернативных способов удержания RDP-сессий (требуется для работы робота с рабочим столом).

Два варианта работы по удержанию RDP-сессии отображены на схеме:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-10.PNG>)

### Удержание одной RDP-сессии в консоли
Для этого нужно файл `restore_console.bat` из комплекта поставки разместить в корне диска `C:\`. 
Закрывать RDP-сессию необходимо при помощи запуска этого файла из cmd. Для автоматизации этого запуска, чтобы он проводился автоматически при отключении 
пользователя от сессии, можно создать Windows Task на событие «On disconnect on user session».

На основе импорта из файла `RDP-Disconnector.xml` нужно создать Windows Task:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-11.PNG>)

Проверяем свойства создаваемой Windows Task «RDP-Disconnector»:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-12.PNG>)

Windows Task «RDP-Disconnector» должна работать под локальным администратором:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-13-1.PNG>)

Проверяем наличие созданной Windows Task «RDP-Disconnector»:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-13.PNG>)

### Удержание многих RDP-сессий за счет внешних RDP-подключений

Для этого используется дополнительный сервис. 

Сначала заводятся пользователи для RDP-сессий, например, user1 и user2: 

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-14.PNG>)

Пользователи желательно должны входить в группу Administrators:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-15.PNG>)

Если пользователи не входят в группу Administrators, то обязательно (!) должны входить в группы Users и Remote Desktop Users.

Добавленные пользователи должны быть зарегистрированы для машины робота (имя пользователя/пароль, и т.д.) в Оркестраторе:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-16.PNG>)

В Оркестраторе для RDP-пользователя должны быть настроены параметры безопасности подключения:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-17.PNG>)

Параметры RDP-подключения:
1. [AuthenticationLevel](https://docs.microsoft.com/en-us/windows/win32/termserv/imsrdpclientadvancedsettings4-authenticationlevel) – 1 
2. [NegotiateSecurityLayer](https://docs.microsoft.com/en-us/windows/win32/termserv/imsrdpclientnonscriptable3-negotiatesecuritylayer) – true
3. [EnableCredSspSupport](https://docs.microsoft.com/en-us/windows/win32/termserv/imsrdpclientadvancedsettings6-enablecredsspsupport) – true
4. DesktopWidth – Разрешение экрана по ширине (1920).
5. DesktopHeight – Разрешение экрана по высоте (880).
6. ColorDepth – Цветопередача (32).

К машине робота должны быть разрешены RDP-подключения:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-18.PNG>)

Также должны быть настроены параметры подключения, открыт порт для RDP (порт должен быть открыт и в случае единственного пользователя):

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-19.PNG.png>)

Если используется сервер удаленных рабочих столов, то необходимо его настроить. Запустить оснастку gpedit.msc (Win+R) :

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-20.PNG>)

На вкладке Security:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-21.PNG>)

На вкладке Connections:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-22.PNG>)

Блокировка экрана пользователя должна быть отключена. Локально, или через групповые политики AD:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-23.PNG>)

Сервис RDP-подключений запускается на внешней машине, например, на машине с WebApi. На одну сессию сервис расходует порядка 100 Мб памяти.

RDP-сессии запускаются автоматически при старте роботов. Этот процесс требует некоторого времени, в течение которого робот должен подождать открытия. Эти параметры задаются в конфиге WebApi:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-24.PNG>)

Продолжительность ожидания запуска RDP-сессии:

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-25.PNG>)

Если в RPA-проекте (zip-архив) присутствуют файлы с кириллицей в наименовании, то для корректной распаковки архива перед запуском робота необходимо чтобы в конфигурационном файле службы Агента был настроен параметр ProjectZipEncoding. 
Наиболее востребованные значения:  utf-8 (для Windows), cp866 (для Linux) и null (кодировка по умолчанию в ОС).

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-26.PNG>)

## Настройка машины робота из скрипта

Настройку машины робота можно выполнить посредством PowerShell-скрипта `PrimoWorker.ps1`, который входит в комплект поставки Оркестратора. 

В скрипте нужно установить значения переменных в секции Input. Все необходимые комментарии содержатся в самом скрипте.

![](<../../../../orchestrator-new/resources/install/windows/setting-up-machines-win/appendix-27.PNG>)

Необходимо разрешить выполнение неподписанного скрипта, выполнив перед его запуском в PowerShell команду:
```
>Set-ExecutionPolicy Bypass -Scope Process -Force
```
Запускаем скрипт `PrimoWorker.ps1` и дожидаемся окончания его выполнения. Проверяем настройку машины робота.

