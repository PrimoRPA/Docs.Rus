---
description: Руководство пользователя
---

# Primo RPA

![](<.gitbook/assets/logo_primo.png>)

**Primo RPA** — это российское программное решение для роботизации бизнес-процессов.

Система Primo RPA позволяет:
* Сократить себестоимость процессов за счет передачи роботу рутинных, повторяемых операций.
* Выполнять роботизируемые операции быстрее, обеспечивая рост прибыли и лояльности клиентов. 
* Снижать число ошибок, вызванных «человеческим фактором».

## Состав системы
В состав системы входят следующие программы: 
* Primo RPA Studio (также Studio, Студия);
* Primo RPA Robot (также Robot, Робот);
* Primo RPA Orchestrator (также Orchestrator, Оркестратор);
* Primo RPA Idea Hub (также Idea Hub);
* Primo RPA AI Server (также AI Server).

## Функциональные возможности
### Primo RPA Studio

Primo RPA Studio — основной инструмент для разработки роботов. Именно здесь аналитики и разработчики собирают RPA-сценарий, используя как готовые компоненты, так и компоненты собственной разработки. 

**Ключевые возможности:**
1. Создание сценария для робота. Разрабатывать сценарий можно в виде последовательности операций, диаграммы или в чистом коде, что позволяет роботизировать сценарии практически любой сложности. Набор сценариев составляет единый RPA-проект, в рамках которого доступна группировка сценариев по папкам. 
2. Отладка сценария. Позволяет протестировать сценарий через Студию и отследить результаты выполнения в Консоли. Помогает проанализировать и исправить ошибки в сценариях до публикации проекта.
4. Использование зависимостей. Возможно обращаться к дополнительным библиотекам при работе с RPA-проектом. Доступна возможность разрабатывать, опубликовывать и использовать собственные библиотеки в проекте.
5. Шаблоны проекта. Возможность сделать из готового проекта шаблон, который будет применяться при создании новых проектов. 
6. Шаблоны поиска. Используются для взаимодействия с пользовательским интерфейсом программ. Позволяют идентифицировать компонент приложения, чтобы получить к нему программный доступ.
7. Запись сценария. Имеется функция записи пользовательских действий для упрощения формирования сценария.
8. Запись трафика. Помогает быстро и легко анализировать обмен с порталами, сайтами и веб-сервисами, а также формировать Web-запросы в сценариях на основе полученных данных.
9. Импорт проектов. Возможность импортировать проекты в Студию из других RPA-платформ: например, UiPath, Blue Prism.
10. Интеграция с Оркестратором. Позволяет получать лицензии на Студию через Оркестратор, а также публиковать готовые проекты в Оркестраторе.

### Primo RPA Robot

Primo RPA Robot — это робот, выполняющий заданные пользователем сценарии. Поддерживает работу как в среде Windows, так и в Linux, что особенно важно для компаний, активно использующих рабочие места на базе отечественных операционных систем типа Astra Linux.

С приложением Primo RPA Robot возможно работать как из командной строки, так и через графический интерфейс пользователя (GUI). Работа через GUI осуществляется с помощью утилиты Primo RPA Robot Runner, которая входит в комплект поставки. Также управлять роботом можно из Оркестратора — подробнее об этом см. в функциональных возможностях Primo RPA Orchestrator.

**Возможности Primo RPA Robot**:
1. Ручной запуск выполнения RPA-проектов. 
3. Интеграция с Оркестратором. Функция для обмена данных с Оркестратором.
4. Запись логов и пользовательских событий в журнал. 

**Возможности утилиты Primo RPA Robot Runner**:
1. Предоставляет графический интерфейс пользователя для работы с Primo RPA Robot.
2. Автоматический запуск задач на выполнение RPA-проектов. Возможно настраивать расписания и запускать задачи автоматически в соответствии с графиком.
4. Работа со станциями. Предоставляет базовый функционал для управления RDP-сессиями.

### Primo RPA Orchestrator 

Primo RPA Orchestrator — предназначен для автоматизации запуска RPA-проектов на множестве развернутых в организации роботов и для управления роботами. Оркестратор позволяет задавать расписание работы роботов, контролировать их работу. Для поддержки работы крупных компаний с несколькими независимыми группами пользователей Primo RPA Orchestrator предоставляет возможность «изолировать» группы роботов друг от друга. За счет поддержки мультитенантности пользователь каждой группы будет видеть и управлять только своими роботами, без возможности влияния на роботов других групп.

**Ключевые возможности:**
1. Централизованное управление лицензиями на продукты Primo RPA. Получение и установка лицензий на выбранные продукты, управление ими через интерфейс Оркестратора.
2. Централизованное управление роботами. Развертывание и настройка роботов, их логирования, регистрация машин роботов, разбиение роботов на группы для независимого управления, возможность привязки к роботу RDP-пользователя.
3. Добавление проектов. Загрузка RPA-проектов, созданных в Студии, для дальнейшего выполнения роботом (-ами). Возможно привязать роботов определенных версий к проекту.
4. Автоматизация запуска RPA-проектов при помощи заданий. Управление запуском заданий при помощи триггеров. В качестве триггера, например, может выступать расписание, согласованное с производственным календарем организации.
5. Стратегия назначения роботов на выполнение RPA-проекта. Возможно определить порядок назначения Роботов на задание при автоматическом запуске проекта. 
6. Ручной запуск робота с RPA-проектом. Возможность выбрать развернутого робота и вручную запустить выполнение проекта.
7. Работа с очередями обмена данных. Очереди используются для организации обмена данными между роботами, а также между роботами и Студией при выполнении RPA-проектов. 
8. Мультитенантность. Возможность создавать тенанты - филиалы организации для изолированного доступа к сущностям системы. В рамках тенанта доступно управление машинами роботов и пользователями тенанта.
9. Управление пользователями. Создание учетных записей и назначение пользователям ролей для разграничения прав доступа. Доступна интеграция с Active Directory - она позволяет не заводить пользователей в системе, а использовать учетные записи из AD.
10. Мониторинг. Для осуществления мониторинга в системе имеются 3 журнала событий: для Оркестратора, роботов и проектов. Просмотр журналов доступен через UI Оркестратора. Для аналитики по журналам может применяться внешняя аналитическая система Grafana - не является частью Оркестратора, поставляется как дополнение к нему.

### Primo RPA Idea Hub

Primo RPA Idea Hub — это программный продукт для комплексного управления процессом роботизации. Встроенный инструментарий позволяет производить сбор и анализ предложений по роботизации процессов внутри организации, оценку эффективности и мониторинг статуса реализации задач.

**Ключевые возможности:**
1. Упрощение взаимодействия между всеми участниками процесса роботизации.
2. Интеграция с платформой Primo, что обеспечивает сбор данных из других продуктов линейки для целей планирования и анализа.
3. Hosted или он-прем интеграция с инфраструктурой компании-заказчика.
4. Настраиваемая ролевая модель доступа, с поддержкой AD и SSO.
5. Гибко настраиваемый UI, кастомизация под требования и метрики заказчика.
6. Визуальное представление эффектов роботизации.
7. Возможности импорта данных из других продуктов и ИТ-систем, а также экспорта в них. 

### Primo RPA AI Server

Primo RPA AI Server — интеллектуальная среда для обучения и использования алгоритмов искусственного интеллекта (ИИ). Сервис позволяет использовать возможности ИИ, такие как сверточные нейросети и большие языковые модели (LLM), для обработки неструктурированной информации в виде изображений и текста. Обученные модели могут быть использованы в процессах RPA.

**Ключевые возможности:**
1. Обучение моделей для работы с любыми типами документов. 
1. Встроенные инструменты для разметки документов, на которых планируется обучать модели.
1. Классификация смешанных изображений по типам документов.
1. Распознавание данных в документах и получение результата в структурированном виде по заранее определенной схеме. 
1. Использование обученных моделей в процессах RPA или во внешних системах через API.
1. Масштабирование количества используемых моделей за счет агентов.
1. Мониторинг состояния моделей и компонентов сервиса.

## Системные требования

Компанией Primo RPA разрабатываются версии продуктов, предназначенные для работы с операционными системами Windows и Linux. 
Продукты для операционной системы Линукс аккредитованы для использования и внесены в список совместимого программного обеспечения для следующих российских операционных систем:
* [РЕД ОС 7+](https://redos.red-soft.ru/compatible/?SECTION=&q=Primo) (результаты испытаний подтверждены [сертификатами совместимости](https://primo-rpa.ru/tpost/y627gjkdj1-platforma-primo-rpa-poluchila-akkreditat))
* [Astra Linux](https://astralinux.ru/ready-for-astra/compatible-software/28792/)

### Studio

Для установки и эксплуатации ПО Primo RPA Studio существуют следующие требования к компьютеру пользователя.

| Аппаратные требования    |  Программные требования  |
| ------------ | ------------- |
| CPU 4 ядра, RAM 8 Гб, HDD 100 Гб | <p>Microsoft Windows 7 (SP2) и выше. </p> <p>Microsoft .NET Framework 4.6.1; Microsoft Visual C++ Runtime 14; Windows PowerShell.</p> <p>Права локального администратора (в зависимости от используемых компонентов)</p> |

### Studio Linux

Для установки и эксплуатации ПО Primo RPA Studio Linux компьютер пользователя должен соответствовать требованиям из таблицы.

|                         |     Минимальные     |      Рекомендуемые    |
| ----------------------- | ------------------- | ----------------------|
| CPU                     |        2 ядра       |         4 ядра        |
| Оперативная память      | 4 Гб (возможно существенное замедление работы) |  8 Гб и выше |   
| Свободное место на HDD  | 64 Гб + 10 Гб (+ 10 Гб на каждую учетную запись) | 100 Гб + 10 Гб (+ 10 Гб на каждую учетную запись) |
| Монитор                 | 1280 x 720 | 1920 x 1080 или выше |

### Robot

Для установки и эксплуатации ПО Primo RPA Robot (работающего как с Оркестратором, так и без него) существуют следующие требования к машине робота.

| Аппаратные требования | Программные требования | 
| --------------------- | ---------------------- | 
| CPU 8 ядер, RAM 8 Гб, HDD 250 Гб  | Windows 10 / Windows Server 2016 и выше | 
| CPU 6 ядер, RAM 8 Гб, HDD 250 Гб  | Linux: CentOS 8+, Ubuntu 20+, Astra Linux 1.7+ | 

### Orchestrator

Для установки и эксплуатации ПО Primo RPA Orchestrator существуют следующие требования.

| Компоненты сервера   | Аппаратные требования  | Программные требования  |
| -------------------- | ---------------------- | ----------------------- |
| Сервер Оркестратора  | CPU 8 ядер, RAM 16 Гб, HDD 200 Гб  | Windows Server 2016 и выше. <p>Linux: CentOS 8+, Ubuntu 20+, Astra Linux 1.7+ </p> |
| Сервер БД            | CPU 8 ядер, RAM 16 Гб, HDD 200 Гб  | см. выше |
| Сервер журнала       | CPU 8 ядер, RAM 16 Гб, HDD 1000 Гб | см. выше |

### Idea Hub

Для установки и эксплуатации ПО Primo RPA Idea Hub существуют следующие минимальные и рекомендованные требования.

Минимальные:

| Аппаратные требования    |  Программные требования  |
| ------------ | ------------- |
| CPU 2 ядра, 2GHz, RAM 4 Гб, HDD 50 Гб | <p>Ubuntu 22.04 64 бита, CentOS 8 64 бита или аналогичные;</p> 	<p>Windows Server 2016, 2019</p> |

Рекомендованные:

| Аппаратные требования    |  Программные требования  |
| ------------ | ------------- |
| CPU 4 ядра, 4GHz, RAM 8 Гб, HDD 200 Гб | <p>Ubuntu 22.04 64 бита, CentOS 8 64 бита или аналогичные;</p> 	<p>Windows Server 2016, 2019</p> |


### AI Server

Для установки и эксплуатации ПО Primo RPA AI Server существуют следующие системные требования.

#### Требования к машине сервера 

Для сервера требуется машина под управлением Astra Linux 1.7+. 


| Параметр         | Рекомендуемые                  |
| ---------------- | ------------------------------ | 
| CPU              | x86/x64, 8 ядер                |                  
| RAM              | 8 Гб                 |      
| Хранилище        |  200 Гб (ОС + базовые данные приложений) <p> Дополнительно:</p> <p> + ~1-2 Гб для обучения 1 модели; </p> <p> +  ~1 Гб в сутки при обработке 1000 изображений </p> |           


#### Требования к целевой машине

Для целевой машины требуется рабочая станция под управлением Astra Linux 1.7+. 

| Параметр   | Минимальные        |  Рекомендуемые                     | Высокопроизводительные  |
| ---------- | ------------------ | ---------------------------------- | ----------------------- |
| CPU        | Intel Core i5 / AMD Ryzen 5 | Intel Core i7/i9 / AMD Ryzen 7/9 | Intel Xeon / AMD EPYC |
| Кол-во физических ядер на 1 агента | 4 (возможно замедление обучения модели) | 8 | 16          |
| RAM        | 8 ГБ               | 32 ГБ                              | 64 ГБ                   | 
| Хранилище  | 1Tb HDD ТБ (OS + Data) | 2Tb SSD                            | NVMe SSD или RAID       | 
| GPU        | - | NVIDIA GPU семейства Ampere (compute capability > 8.0) VRAM > 16 | NVIDIA GPU семейства Ampere (compute capability > 8.0) (например, RTX 3090) | 
| CUDA       | -                  | 12.1                               | 12.1                    | 
