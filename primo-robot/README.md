# Робот

Робот предназначен для запуска задач, в рамках которых исполняются RPA-проекты, созданные в приложении Primo Studio.

Работа с Роботом может быть построена несколькими способами:

1. Автоматически через Оркестратор - см. раздел [Оркестратор](https://docs.primo-rpa.ru/primo-rpa/orchestrator/intro) данного сайта.
2. Вручную на компьютере пользователя с помощью приложения **Primo Robot**. 
3. Вручную или автоматически на компьютере пользователя через приложение **Robot Runner**. 

Данный раздел посвящен работе с Роботом при помощи программ Primo Robot и Robot Runner.

## Отличие Primo Robot от Robot Runner

**Primo Robot** - самостоятельное приложение с минимальным графическим интерфейсом. Запуск задач осуществляется через командную строку. Primo Robot не поддерживает запуск задач по расписанию.

**Robot Runner** - специальная утилита, позволяющая запускать Робота без Оркестратора и командной строки. Это более удобный способ запуска Робота, поскольку приложение обладает графическим интерфейсом пользователя. Через Robot Runner можно настроить запуск задач по расписанию.\
Приложение корректно работает только при условии, что Primo Robot также был установлен на компьютере пользователя, т.е. оно не является самостоятельным, в отличие от Primo Robot.

### Издания

Робот выпускается в двух изданиях (то же, что и лицензии):

* **Enterprise:** полное издание. Доступна внешняя поддержка Рабочего стола через RDP-соединения. Запрос лицензии Enterprise осуществляется через Оркестратор.
* **Desktop:** Робот данного типа предназначен для работы с локальной машиной и должен быть установлен на рабочем месте пользователя. Для него недоступна поддержка Рабочего стола через RDP-соединения. Лицензию можно запросить как через Оркестратор, так и локально с компьютера пользователя при запуске Робота.

> **Примечание**. Ранее также была доступна лицензия Standard (усеченное издание), но в настоящее время она устарела. Запросить ее более невозможно.

Оба типа лицензий можно использовать для работы с Роботом через Primo Robot или Robot Runner.

### Установка и использование

**Запуск и регистрация в автономном режиме:**

1. [Ручная установка Primo Robot на компьютер пользователя - ОС Windows](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation). 
2. [Ручная установка кроссплатформенной версии Primo Robot](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation/robot_core).
3. [Запуск и регистрация Робота локальным ключом - через Robot Runner](https://docs.primo-rpa.ru/primo-rpa/primo-robot/robot-runner/registration-desktop).
4. [Запуск Робота из командной строки - через Primo Robot](https://docs.primo-rpa.ru/primo-rpa/primo-robot/launch-command).

**Primo Robot Runner:**

1. [Работа с Robot Runner: запуск задач по расписанию без Оркестратора](https://docs.primo-rpa.ru/primo-rpa/primo-robot/robot-runner).

**Запуск и регистрация через Оркестратор:**

1. [Установка Primo Robot через Оркестратор](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/upload-robot). 
2. [Регистрация машины Робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/register-robot).
3. [Типы лицензий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/licensing/license-types) и [Запрос лицензии в Оркестраторе](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/licensing/new-license).
4. [Ручной запуск Робота с RPA-проектом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/robot-manual-start).
5. Автоматизированный запуск RPA-проектов с помощью [Заданий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks) и [Расписаний](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/schedules).

Для более полного понимания работы с Роботом через Оркестратор рекомендуется ознакомиться с документацией из раздела **Оркестратор**.







