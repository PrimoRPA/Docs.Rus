# Введение

Робот предназначен для запуска задач по выполнению RPA-проектов. Проект заранее создается в Primo Studio.

Организовать работу с роботом можно одним из способов:

1. Автоматически через Оркестратор.
2. Вручную на компьютере пользователя через приложение **Primo Robot**.
3. Вручную или автоматически на компьютере пользователя через утилиту **Robot Runner**. 

Данный раздел посвящен работе с роботом при помощи программ Primo Robot и Robot Runner. Робот в данном случае выполняет функцию цифрового ассистента пользователя.

## Отличие Primo Robot от Robot Runner

**Primo Robot** - самостоятельное приложение с минимальным графическим интерфейсом. Запуск задач осуществляется через командную строку. Primo Robot не поддерживает запуск задач по расписанию.

**Robot Runner** - специальная утилита, позволяющая запускать робота без Оркестратора и командной строки. Это более удобный способ запуска робота, поскольку приложение обладает графическим интерфейсом пользователя. Через Robot Runner можно настроить запуск задач по расписанию.\
Приложение корректно работает только при условии, что Primo Robot также был установлен на компьютере пользователя - таким образом, оно не является самостоятельным, в отличие от Primo Robot.

## Издания Primo Robot

Робот выпускается в двух изданиях (то же, что и лицензии):

* **Enterprise:** полное издание. Доступна внешняя поддержка рабочего стола через RDP-соединения. Запрос лицензии Enterprise осуществляется через Оркестратор.
* **Desktop:** робот данного типа предназначен для работы с локальной машиной и должен быть установлен на рабочем месте пользователя. Для него недоступна поддержка рабочего стола через RDP-соединения. Лицензию можно запросить как через Оркестратор, так и локально с компьютера пользователя при запуске робота.

:small_blue_diamond: ***Примечание***. *Ранее также была доступна лицензия Standard (усеченное издание). В настоящее время она является устаревшей, запросить ее более невозможно.*

Оба типа лицензий можно использовать для работы с роботом через Primo Robot или Robot Runner.

### Установка и использование

**Запуск и регистрация в автономном режиме:**

1. [Ручная установка Primo Robot на компьютер пользователя - ОС Windows](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation).   
   * ИЛИ: [Ручная установка кроссплатформенной версии Primo Robot](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation/robot_core).
2. [Регистрация робота локальным ключом](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation/registration-desktop).
3. [Запуск робота из командной строки (через Primo Robot)](https://docs.primo-rpa.ru/primo-rpa/primo-robot/installation/launch-command).
4. [Запуск робота с помощью Robot Runner](https://docs.primo-rpa.ru/primo-rpa/primo-robot/robot-runner).

**Запуск и регистрация через Оркестратор:**

1. [Загрузка дистрибутива робота через Оркестратор](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/robots/upload-robot).
2. [Регистрация машины робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/robots/register-robot).
3. [Регистрация RDP-пользователей на машине робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/robots/register-rdp-users).
4. [Запрос лицензии в Оркестраторе](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/licensing/new-license).
5. Ручной запуск RPA-проекта:
   * [Вручную поместить проект в очередь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/put-project-in-project-queue) - предпочтительный сценарий.
   * [Вручную запустить робота с RPA-проектом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/robot-manual-start) - альтернативный сценарий.
7. Автоматизированный запуск RPA-проектов с помощью [заданий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks) и [расписаний](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks/schedules).

Для более полного понимания работы через Оркестратор рекомендуется ознакомиться с документацией из раздела **Primo Orchestrator**.







