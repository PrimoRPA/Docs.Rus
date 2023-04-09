# Установка RobotLogs как службы 
Раздел содержит инструкцию по установке **RobotLogs как службы** под Windows 2016 Server. В версии Windows 2016 Server среда исполнения ASP .NET Core предустановлена, поэтому возможно сразу перейти к установке RobotLogs. 

**Как установить RobotLogs:**

1\. Сначала требуется установить RabbitMQ (см. раздел «Руководство по установке RabbitMQ под Windows 2016 Server»).\
2\. Разархивируем `C:\Install\RobotLogs.zip` в `C:\Primo\RobotLogs`. Можно при помощи PowerShell:
```
> $InstallPath = "C:\Install"
> Expand-Archive -LiteralPath "$InstallPath\RobotLogs.zip" -DestinationPath "C:\Primo\RobotLogs " -Force
```
3\. Создаем системную переменную окружения (если не создана ранее). Для этого в PoweShell выполняем команду:
```
> [System.Environment]::SetEnvironmentVariable('ASPNETCORE_ENVIRONMENT', 'ProdWin', [System.EnvironmentVariableTarget]::Machine)
```
4\. Настраиваем конфигурационный файл:
* Настраиваем строки подключения в БД:

![](<../../../.gitbook/assets/>)

* Настраиваем **UserName** и **Password** сервера RabbitMQ, который используется для обработки логов со скринами рабочего стола:

![](<../../../.gitbook/assets/>)

* Настраиваем **Host, UserName** и **Password** сервера RabbitMQ, который используется для интеграции с Оркестратором:

![](<../../../.gitbook/assets/>)

* Открываем **порт 5672** на файерволе сервера RabbitMQ, который используется для интеграции с Оркестратором.\
  Сервер RabbitMQ, который используется для интеграции с Оркестратором, общий для очередей Primo.Orchestrator.RobotLogs и Primo.Orchestrator.WebApi. Поэтому требуется соблюдать соответствие названий очередей и обменников.

* Настраиваем **URL** Оркестратора (при необходимости, можно поменять пароль встроенной системной записи Orchestrator – одновременно через UI Оркестратора и в этой секции конфигурационного файла):

![](<../../../.gitbook/assets/>)

* Настраиваем **ScreenFilePath** – путь до файлов со скринами рабочего стола, которые собираются с машины робота. Папка по этому пути должна быть создана заранее и на неё должны быть настроены права на чтение и запись для всех:

![](<../../../.gitbook/assets/>)

* Настраиваем в соответствии с конфигом WebApi список тенантов:

![](<../../../.gitbook/assets/>)

5\. Регистрируем **Primo.Orchestrator.RobotLogs.exe** как службу Windows и сразу запускаем ее. Она должна работать как локальная служба. Для этого в PowerShell последовательно выполняем команды:
```
> New-Service -Name Primo.Orchestrator.RobotLogs -BinaryPathName "C:\Primo\RobotLogs\Primo.Orchestrator.RobotLogs.exe" -Description "Primo.Orchestrator.RobotLogs" -DisplayName "Primo.Orchestrator.RobotLogs" -StartupType Automatic 
> $s = Get-Service "Primo.Orchestrator.RobotLogs"
> $s.Start()
```
6\. Созданная служба **Primo.Orchestrator.RobotLogs** будет отображаться в списке всех служб как запущенная.

7\. Открываем порт 56748 на файерволе (если служба RobotLogs не на одном сервере с nginx для WebApi).

8\. Проверяем, что в конфигурационном файле nginx настроено проксирование на RobotLogs (или аналогично настроено в IIS для узла UI, если используется IIS):

![](<../../../.gitbook/assets/>)

![](<../../../.gitbook/assets/>)

9\. В конфигурационном файле **Primo.Orchestrator.WebApi** переключаем прием логов на сервис RobotLogs и перезапускаем **Primo.Orchestrator.WebApi**:

![](<../../../.gitbook/assets/>)

10\. Если запросы в RobotLogs проксируются через отдельный от WebApi эндпоинт, нужно указать в конфиге Primo.Orchestrator.WebApi этот эндпоинт в параметре **RobotLogsBaseUrl**:

![](<../../../.gitbook/assets/>)

***В настоящее время не поддерживается. Зарезервирован для дальнейшей оптимизации приема логов от роботов.***

11\.  Тонкая настройка производительности приема логов настраивается в секции **InputBufferRobotLogs**:

![](<../../../.gitbook/assets/>)

**MaxQueueLength** – максимальный размер входного буфера приема логов от робота. Чем выше, тем больший размер пачек логов робот без потерь может слать в Оркестратор.\
**MaxBatchSize** – максимальный размер пачки за один раз сбрасываемый сервисом в БД ltoolslogs. Чем выше, тем меньше обращений в БД потребуется, но тем большее количество данных за один раз должно быть передано.\
**ThreadSleep** – время (мсек) опроса входного буфера.

:white_check_mark: **Готово**: приложение RobotLogs успешно установлено в качестве службы Windows.
