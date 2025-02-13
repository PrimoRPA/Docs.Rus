# Комплект поставки

Оркестратор поставляется в указанной ниже комплектации\*. Дистрибутивы роботов не входят в комплект поставки и распространяются отдельно. 

> \* *Может меняться в зависимости от конкретной поставки.*

| №п/п | Наименование файла | Описание |
| --- | --- | --- |
| 1. | WebApi.zip | Для развертывания как службы Windows |
| 2. | WebApi-IIS.zip |Для развертывания под IIS |
| 3. | WebApi-linux.zip |Включает файл службы |
| 4. | States.zip |   |
| 5. | States-linux.zip | Включает файл службы |
| 6. | Notifications.zip | Notifications  |  |
| 7. | Notifications-linux.zip | Включает файл службы |
| 8. | nginx-1.21.1.zip | Включает конфигурационный файл nginx (nginx.conf) и файлы самоподписанного SSL-сертификата для https (cert1.crt, cert1.rsa) |
| 9. | nginx-linux.zip |  |
| 10. | UI.zip | Файлы UI Оркестратора в браузере, SPA |
| 11. | dotnet-hosting-8.0.6-win.exe |  Для хостинга NET 8-приложения под IIS | 
| 12. | rewrite_amd64_en-US.msi | Модули IIS, обеспечивающие функциональность реверс-прокси | 
| 13. | requestRouter_amd64.msi |  |
| 14. | postgresql-13.4-1-windows.zip | PostgreSQL | 
| 15. | postgresql-13-linux.zip |  |
| 16. | pg_ms.sh | Для кластера Postgres под Linux |
| 17. | MSSQL.zip |  MS SQL SERVER 2019 | |
| 18. | timescaledb-postgresql-13_2.4.1-windows-amd64.zip | TimescaleDB |
| 19. | timescaledb-postgresql-13-linux.zip |  |
| 20. | rabbitmq.zip | RabbitMQ server. Включает Erlang |
| 21. | rabbitmq-linux.zip |  |
| 22. | Agent.zip | Agent  |
| 23. | Agent-linux.zip |  |
| 24. | PowerShell 7.1.3 | |
| 25. | PrimoWorker.ps1 | PowerShell-скрипт для автоматизации настройки машины Робота и развертывания Агента |
| 26. | ChromeStandaloneSetup64.exe | Браузер Google Chrome |
| 27. | PasswordEncryptor.zip | Программа для шифрования паролей в конфигурационных файлах | 
| 28. | grafana-8.0.6.windows-amd64.msi | Внешняя аналитическая система Grafana. Не является компонентом Оркестратора |
| 29. | Report-RobotCompletes.zip | Примеры дашбордов в Grafana | 
| 30. | Report-Robots.zip |  |
| 31. | Report-RpaProjects.zip |   |
| 32. | syncthing-linux-amd64-v1.18.2.tar.gz | Программа синхронизации папок. Для синхронизации папок с дистрибутивами робота и дампами Журнала |
| 33. | syncthing.service |  |
| 34. | syncthing-windows-amd64-v1.18.2.zip | |
| 35. | RDP-Disconnector.xml | Windows Task для восстановления сеанса после отключения RDP. Используются вместе |
| 36. | restore_console.bat | Скрипт для перенаправления RDP-сессии в консоль |
| 37. | web.config | Должен использоваться при развертывании UI под IIS | |
| 38. | MachineInfo.zip | Служба определения параметров оборудования для работы лицензий | 
| 39. | MachineInfo-linux.zip | |
| 40. | LogEventsWebhook.zip | Служба Webhooks на события Оркестратора | 
| 41. | LogEventsWebhook-linux.zip |   |
| 42. | haproxy.zip |  HAProxy. Только для Linux. Включает конфигурационный файл, файлы сертификата |
| 43. | pg_cron_13-1.3.0-1.rhel8.x86_64.rpm | Расширение PostgreSQL для выполнения заданий по расписанию для Linux |
| 44. | AgentInstaller.zip | Инсталлятор для машины робота. Включает автоматическую регистрацию машины робота в Оркестраторе |
| 45. | RDP2.zip | Служба поддержки активных RDP-сессий |
| 46. | RDP2-linux.zip | |
| 47. | RobotLogs.zip | Служба приема логов от роботов |
| 48. | RobotLogs-linux.zip |  |
| 49. | scr2.ps1 | Скрипт открытия теневой RDP-сессии | 
| 50. | logstash.7z | logstash | 
| 51. | NuGet2.zip | NuGet-сервер | 
| 52. | NuGet2-linux.zip | | 
| 53. | reset-ExchangeQueueStatistics-postgres.sql | Пересчет статистики по очередям обмена данными | 
| 54. | reset-ExchangeQueueStatistics-mssql.sql |  |
| 55. | Analytic.zip | Cлужба сбора аналитики по событиям Оркестратора | 
| 56. | Analytic-linux.zip | |


## Варианты развертывания компонентов

Возможные варианты развертывания компонентов приведены [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/deployment/component-deployment-options).

