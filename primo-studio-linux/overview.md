# Primo Studio Linux

**Primo RPA Studio** - это основной инструмент для разработки роботов. Именно здесь аналитики и разработчики собирают RPA-сценарий, используя как готовые компоненты, так и компоненты собственной разработки.

Компанией Primo RPA разрабатываются версии продукта Primo Studio, предназначенные для работы с операционными системами Windows и Linux. Информацию о версии Primo Studio для Windows можно найти [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/common/editions).

Primo Studio для Линукс аккредитован для использования и внесен в список совместимого программного обеспечения для следующих операционных систем:
* [РЕД ОС](https://redos.red-soft.ru/compatible/?SECTION=&q=Primo) (результаты испытаний подтверждены [сертификатами совместимости](https://primo-rpa.ru/tpost/y627gjkdj1-platforma-primo-rpa-poluchila-akkreditat))
* [Astra Linux](https://astralinux.ru/ready-for-astra/compatible-software/28792/)
* [РОСА Линукс](https://rosa.ru/tech-partners/) (результаты испытаний подтверждены [сертификатами совместимости](https://primo-rpa.ru/solutions/tpost/vp40ndl951-produkti-primo-rpa-uspeshno-sertifitsiro))

Версия продукта Primo Studio для Линукс в данный момент отличается по своим функциональным возможностям от версии для Windows и не является ее полноценным аналогом; часть функциональности находится в процессе разработки.

**Возможности Primo RPA Studio Linux:**

* Поддержка трех режимов разработки RPA-проектов: диаграммы, последовательности и “только код”
* Разработка на C#, Python, JavaScript
* Полноценная интеграция с пакетом Мой Офис 
* Поддержка Open Document Format (ODF, OXML) 
* Работа с почтой (Exchange, IMAP, POP3, SMTP)
* Автоматизация UI: браузеры, десктопные приложения
* Встроенные инструменты работы с базами данных и HTTP запросами
* Интеграция с Primo Orchestrator
* Мощный отладчик
* Поддержка Git
* Возможность создавать свои Nuget-пакеты с помощью SDK
* Технологии: SQL, FTP, HTTP, API

**Некоторые отличия от версии для Windows:**
 
* Значительно более широкое использование командной строки: для запуска Студии, для установки зависимостей, для задания прав
* Версия Primo Studio Linux основана на .Net 8.0, вследствие чего возникает несовместимость Nuget-пакетов, разработанных для фреймворка 4.6.1 (т.е. для версии Студии для Windows) 
* **!!ВАЖНО!! Не гарантируется работоспособность в версии Студии для Linux тех проектов, которые изначально были созданы в версии Студии для Windows. Такие проекты либо требуют доработки, либо должны быть полностью переписаны.**
* Отличия во взаимодействии с пользовательским интерфейсом, так как отсутствует Windows WPF (и, как следствие, отсутствует фреймворк для UI automation), но при этом имеются в наличии множество других графических фреймворков
* Отсутствует привычная экосистема Майкрософт (пакеты MS Office, VBA скрипты и т.д.)
* Использование фреймворка Avalonia для пользовательского интерфейса
* Новая вкладка UI Explorer (Инспектор UI)
* Новые зависимости с открытым кодом

**Возможности Робота:**

* Работа с PDF
* Поддержка современных браузеров
* Автоматизация десктопных приложений (ATSPI)
* Автоматизация консольных приложений
* Взаимодействие с пользователями
* Поддержка работы с OCR
* Работа с файловой системой
