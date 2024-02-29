# Тонкая настройка
Тонкая настройка Оркестратора осуществляется в конфигурационном файле WebApi:
* appsettings.ProdWin.json - для WebApi под Windows (папка `Distr` > `Windows`);
* appsettings.ProdLinux.json - для WebApi под Linux (папка `Distr` > `Linux`).

В тонкую настройку входят возможности:
1. [Внешняя поддержка RDP-сессии](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/rdp-sessions).
1. [Отключение/разлогинивание RDP-сессий ](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/disabling-rdp-sessions).
1. [Множественные производственные календари](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/multiple-production-calendars).
1. [Блокировка робота агентом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/blocking-robot-by-agent).
1. [Настройка очереди проектов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-queue).
1. [Кэширование проекта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-caching).
1. [Таймаут, после которого робот переходит в состояние «Не доступен»](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/robot-state).
1. [Настройка папки для дампа секций журналов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/log-section-dump-folder).
1. [Стратегия очереди проектов для тенанта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-queue-strategies-for-tenant).

