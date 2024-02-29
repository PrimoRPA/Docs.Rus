# Тонкая настройка
Тонкая настройка Оркестратора осуществляется в конфигурационном файле WebApi:
* appsettings.ProdWin.json - для WebApi под Windows (папка `Distr` > `Windows`);
* appsettings.ProdLinux.json - для WebApi под Linux (папка `Distr` > `Linux`).

В тонкую настройку входят возможности:
1. [Внешняя поддержка RDP-сессии](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/rdp-sessions).
1. [Отключение/разлогинивание RDP-сессий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/disabling-rdp-sessions).
1. [Трансляция RDP-сессии](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/broadcast-rdp-session).
1. [Таймаут, после которого робот переходит в состояние «Не доступен»](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/robot-state).
1. [Блокировка робота агентом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/blocking-robot-by-agent).
1. [Отключение тенанта по умолчанию и блокировка встроенных учетных записей](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/disable-default-tenant).
1. [Стратегия очереди проектов для тенанта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-queue-strategies-for-tenant).
1. [Очереди проектов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-queue).
1. [Кэширование проекта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-caching).
1. [Очистка старых запусков проектов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/setting-up-old-runs-cleaning).
1. [Множественные производственные календари](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/multiple-production-calendars).
1. [Настройка папки для дампа секций журналов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/log-section-dump-folder).
1. [Физическое удаление элементов очереди обмена данными](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/physic-removing-items).
1. [Ограничение версии Студии](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/limit-studio-version).
1. [Ограничение потока событий от триггеров](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/limit-thread-of-events-from-triggers).
1. [Параметры оповещений](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/notification-settings).
