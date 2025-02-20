# Введение

Робот предназначен для запуска задач по выполнению RPA-проектов. Проект заранее создается в Primo RPA Studio.

Организовать работу с роботом можно одним из способов:

1. Автоматически через Оркестратор.
2. Вручную на компьютере пользователя через приложение **Primo RPA Robot**.
3. Вручную или автоматически на компьютере пользователя через утилиту **Robot Runner**. 

Данный раздел посвящен работе с роботом при помощи программ Primo RPA Robot и Robot Runner. Робот в данном случае выполняет функцию цифрового ассистента пользователя.

## Чем Primo RPA Robot отличается от Robot Runner

**Primo RPA Robot** — самостоятельное приложение с минимальным графическим интерфейсом. Запуск задач осуществляется через командную строку. Primo RPA Robot не поддерживает запуск задач по расписанию.

**Robot Runner** — специальная утилита, позволяющая запускать робота без Оркестратора и командной строки. Это более удобный способ запуска робота, поскольку приложение обладает графическим интерфейсом пользователя. Через Robot Runner можно настроить запуск задач по расписанию.

Утилита Robot Runner корректно работает только при условии, что Primo RPA Robot также был установлен на компьютере пользователя — таким образом, оно не является самостоятельным, в отличие от Primo RPA Robot.

## Издания Primo RPA Robot

Робот выпускается в двух изданиях (то же, что и лицензии):

* **Enterprise** — полное издание. Доступна внешняя поддержка рабочего стола через RDP-соединения. Запрос лицензии Enterprise осуществляется через Оркестратор.
* **Desktop** — робот данного типа предназначен для работы с локальной машиной и должен быть установлен на рабочем месте пользователя. Для него недоступна поддержка рабочего стола через RDP-соединения. Лицензию можно запросить как через Оркестратор, так и локально с компьютера пользователя при запуске робота.

{% hint style="info" %}
**Примечание**. Ранее также была доступна лицензия Standard (усеченное издание). В настоящее время она является устаревшей и запросить ее невозможно.
{% endhint %}

Оба типа лицензий можно использовать для работы с роботом через Primo RPA Robot или Robot Runner.

## Установка и использование

**Запуск и регистрация в автономном режиме:**

1. [Установка Primo RPA Robot на компьютер пользователя для ОС Windows](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-robot/installation) 
   * ИЛИ: [Установка кроссплатформенной версии Primo RPA Robot](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-robot/installation/robot_core)
2. [Запрос лицензии Desktop](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-robot/installation/registration-desktop)
3. [Запуск Primo RPA Robot из командной строки](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-robot/installation/launch-command)
4. [Работа с роботом через Robot Runner](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-robot/robot-runner)

**Запуск и регистрация через Оркестратор:**

1. [Загрузка дистрибутива робота через Оркестратор](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/robots/upload-robot).
2. [Регистрация машины робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/robots/register-robot).
3. [Регистрация RDP-пользователей на машине робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/robots/register-rdp-users).
4. [Запрос лицензии в Оркестраторе](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-admin/licensing/new-license).
5. Ручной запуск RPA-проекта:
   * [Поместить проект в очередь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-user/manual-prj-in-queue) — предпочтительный сценарий.
   * [Запустить робота с RPA-проектом](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-user/manual-robot-start) — альтернативный сценарий.
6. Автоматизированный запуск RPA-проектов с помощью [заданий](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-user/tasks-overview) и [расписаний](https://docs.primo-rpa.ru/primo-rpa/orchestrator/orchestrator-user/tasks/tasks-schedules).

Для более полного понимания работы через Оркестратор рекомендуется ознакомиться с документацией из раздела **Primo RPA Orchestrator**.







