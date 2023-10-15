# Комплект поставки

Полный комплект поставки Оркестратора весит ~ 3,5 Гб и содержит: 
* 54 файла дистрибутивов - входят в папку `Distr`;
* 53 файла документации - входят в папку `Docs`. 

Дистрибутивы роботов не входят в комплект поставки и распространяются отдельно. 


## Файлы дистрибутивов 

Оркестратор поставляется в следующей комплектации\*:

> \* *Может меняться в зависимости от конкретной поставки.*

1. **WebApi.zip**. Для развертывания WebApi как службы Windows.
1. **WebApi-IIS.zip**. Для развертывания WebApi под IIS.
1. **WebApi-linux.zip**. Для установки WebApi под Linux. Включает файл службы.
1. **States.zip.** States - служба вычисления системных состояний. Архив включает файл службы.
1. **States-linux.zip**. States для Linux.
1. **Notifications.zip**.	Notifications - служба уведомлений на email. Архив включает файл службы.
1. **Notifications-linux.zip**.	Notifications для Linux.
1. **nginx-1.21.1.zip**. Включает конфигурационный файл Nginx (`nginx.conf`) и файлы самоподписанного SSL-сертификата для HTTPS (`cert1.crt`, `cert1.rsa`).
1. **nginx-linux.zip**. То же, что и выше, но для Linux.
1. **UI.zip**. Файлы UI Оркестратора в браузере, SPA.
1. **dotnet-hosting-7.0.11-win.exe**. Для хостинга NET 7-приложения под IIS.
1. **rewrite_amd64_en-US.msi**. Модули IIS, обеспечивающие функциональность реверс-прокси.
1. **requestRouter_amd64.msi**. Модули IIS, обеспечивающие функциональность реверс-прокси.
1. **postgresql-13.4-1-windows.zip**. PostgreSQL. Включает скрипты начальной настройки БД ltoolslicense (в зависимости от поставки может не включать дистрибутив PostgreSQL - пакеты или установочные файлы).
1. **postgresql-13-linux.zip**. PostgreSQL для Linux. 
1. **pg_ms.sh**. Для кластера Postgres под Linux.
1. **pg_cron_13-1.3.0-1.rhel8.x86_64.rpm**. Расширение PostgreSQL для выполнения заданий по расписанию для Linux.
1. **timescaledb-postgresql-13_2.4.1-windows-amd64.zip.** TimescaleDB - расширение PostgreSQL (Windows).
1. **timescaledb-postgresql-13-linux.zip.** TimescaleDB для Linux.
1. **MSSQL.zip**. MS SQL SERVER 2019. Включает скрипты начальной настройки БД ltoolslicense.
1. **rabbitmq.zip**. RabbitMQ server. Включает Erlang.
1. **rabbitmq-linux.zip**. То же, что и выше, но для Linux.
1. **grafana-8.0.6.windows-amd64.msi**. Внешняя аналитическая система Grafana. Не является компонентом Оркестратора.
1. **Роботы-1627543691525.json**. Пример отчета в Grafana.
1. **v_AllWorked-postgres.sql**. Представление (View) в БД для примера отчета в Grafana. Примечание: PostgreSQL.
1. **v_AllWorked-mssql.sql**. Представление (View) в БД для примера отчета в Grafana. Примечание:	MS SQL Server.
1. **dotnet31-sdk-linux.zip**. Пакеты `dotnet-sdk-3.1`, `aspnetcore-runtime-3.1`.
1. **syncthing-linux-amd64-v1.18.2.tar.gz**. Программа синхронизации папок с дистрибутивами робота и дампами Журнала.
1. **syncthing.service**. Программа синхронизации папок с дистрибутивами робота и дампами журнала.
1. **syncthing-windows-amd64-v1.18.2.zip**. Программа синхронизации папок с дистрибутивами робота и дампами Журнала.
1. **web.config**. Должен использоваться при развертывании UI под IIS.
1. **MachineInfo.zip**. Служба определения параметров оборудования для работы лицензий.
1. **MachineInfo-linux.zip**. См. выше.
1. **LogEventsWebhook.zip**.	Служба Webhooks на события Оркестратора.
1. **LogEventsWebhook-linux.zip**. См. выше.
1. **haproxy.zip**. HAProxy. Только для Linux. Включает конфигурационный файл, файлы сертификата.
1. **RDP2.7.zip**. Служба поддержки активных RDP-сессий.
1. **RDP2-Astra.zip**. См. выше.
1. **RDP2-CentOS.zip**. См. выше.
1. **RobotLogs.zip**. Служба приема логов от роботов.
1. **RobotLogs-linux.zip**. См. выше.
1. **scr2.ps1**. Скрипт открытия теневой RDP-сессии.
1. **logstash.7z**. Утилита Logstash.
1. **NuGet2.zip**. Локальный NuGet-сервер под Windows.
1. **NuGet2-linux.zip**. Локальный NuGet-сервер под Linux.
1. **PasswordEncryptor.zip**. Программа для шифрования паролей в конфигурационных файлах.
1. **AgentInstaller.zip**. Инсталлятор для машины робота под Windows. Включает автоматическую регистрацию машины робота в Оркестраторе.
1. **Agent.zip**. Дистрибутив Агента для Windows. Используется для настройки машины Робота без AgentInstaller.
1. **Agent-linux.zip**. Дистрибутив Агента для Linux.
1. **PowerShell-7.1.3-win-x64.msi**. Установщик PowerShell 7.1.3.
1. **PrimoWorker.ps1**. PowerShell-скрипт для автоматизации настройки машины робота и развертывания Агента.
1. **RDP-Disconnector.xml**. Windows Task для восстановления сеанса после отключения RDP. Запускает файл `restore_console.bat`.
1. **restore_console.bat**. Скрипт для перенаправления RDP-сессии в консоль. Используется вместе с файлом RDP-Disconnector.xml.
1. **ChromeStandaloneSetup64.exe**. Установщик браузера Google Chrome.

Точный размер каждого файла приведен в руководстве «Развертывание Primo RPA 23.x - Руководство администратора.docx». Документ включен в поставку. В нем же можно просмотреть полный перечень всех документов по Оркестратору, входящих в комплект.

## Варианты развертывания компонентов

Возможные варианты развертывания компонентов приведены [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/component-deployment-options).

