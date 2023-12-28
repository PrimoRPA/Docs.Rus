# Развертывание 
Руководство по развертыванию Оркестратора предназначено для системных администраторов, которые обладают следующими знаниями и навыками:

1.	**Обязательно - уверенный пользователь ОС:**
    *	Владеть инструментами ОС для навигации по папкам и файлам.
    * Создавать и редактировать текстовые файлы в стандартном для ОС редакторе.
    * Копировать файлы, копировать текст из файлов, сохранять файлы. 
    * Работать с архиватором ZIP.
    * Знать, что такое BAT-файлы, и уметь их создавать (для Windows).
2.	**Обязательно - опыт администрирования ОС:**
    * Запускать команды ОС и программы из-под Администратора/root.
    * Работать в cmd (Windows).
    * Работать в PowerShell (Windows).
    * Иметь навыки администрирования AD, DNS (Windows). В зависимости от варианта развертывания могут потребоваться навыки администрирования IIS.
    * Иметь навыки установки и администрирования служб.
    * Иметь навыки администрирования пользователей и удаленного доступа.
3.	**Обязательно - минимальный опыт администрирования БД PostgreSQL/MS SQL Server\***:
    * Устанавливать PostgreSQL/MS SQL Server на сервер и производить базовую настройку.
    * Запускать SQL-скрипты. 
4. **Желательно – опыт администрирования БД:**
    * Секционирование таблиц**. 
    * Сбор метрик.
    * Конфигурирование под высокую нагрузку.

> \* *В зависимости от СУБД Оркестратора.*\
> \*\* *Комплект поставки содержит инструкции по секционированию. В том числе для передачи журналов робота в ElasticSearch для последующего долговременного хранения и аналитики по историческим данным.*

## Общая информация

Оркестратор предназначен для развертывания в локальной сети организации. 

Локальная сеть может быть построена на основе AD - службы Active Directory. Интеграция Оркестратора с AD организации позволяет использовать технологию единого входа SSO (Single Sign-On). Настройка интеграции с AD описана [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/AD-integration). 

Если организация состоит из обособленных подразделений/филиалов, Оркестратор может функционировать в мультитенантном варианте. В этом случае филиалу назначается тенант, который можно рассматривать как относительно независимый экземпляр Оркестратора. Настройка мультитенантности описана [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/tenants). 

## Содержание 
В руководство по развертыванию входят разделы:
1. [Компоненты системы](https://docs.primo-rpa.ru/primo-rpa/orchestrator/system-components).
1. [Комплект поставки](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/kit).
1. [Системные требования](https://docs.primo-rpa.ru/primo-rpa/orchestrator/systemreq).
1. [Рекомендации по развертыванию](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/recommendations).
1. [Установка компонентов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/install-orch).
1. [Развертывание сервера приложений на Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/deploy-options).
1. [Контроль целостности конфигурационных файлов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/integrity-of-configs).
1. [Интеграция с Active Directory](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/ad-integration).
1. [Мультитенантность](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/tenants).
1. [Первоначальная настройка](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/initial-setup).
1. [Интеграция с внешними системами](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/integration).
1. [Тонкая настройка](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning):
   * [Внешняя поддержка RDP-сессий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/rdp-sessions).
   * [Отключение RDP-сессий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/disabling-rdp-sessions).
   * [Множественные производственные календари](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/multiple-production-calendars).
   * [Блокировка робота агентом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/blocking-robot-by-agent).
   * [Настройка очереди проектов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/project-queue).
   * [Кэширование проекта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/project-caching)
   * [Сбор состояния роботов по KeepAlive](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/collecting-state-of-robots).
   * [Настройка папки для дампа секций журналов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/log-section-dump-folder).
   * [Настройка стратегии очереди проектов для тенанта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/fine-tuning/project-queue-strategies-for-tenant).




