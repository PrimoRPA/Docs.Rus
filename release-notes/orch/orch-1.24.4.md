# Primo RPA Orchestrator 1.24.4

История изменений в **Primo RPA Orchestrator** для Windows за апрель 2024-го года.

## Обновления и улучшения 

1.







### Улучшения UX/UI


1. На странице **Роботы > Переразвернуть робота** добавлена функциональная кнопка очистки поля **Шаблон развертывания**.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/15531

2. Добавлены новые статусы выполнения роботов. Теперь в веб-интерфейсе Оркестратора доступны статусы **Стартует-Ожидает** и **Завершается работа**.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/13087

3. На странице **RPA-проекты**  во вкладке **Запуски** изменены расположения чекбоксов **Ошибка** и **Архив**

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/10109



## Улучшения в UI 3

1. Исправлены ошибки с отображением статусов транзакций в элементах очереди. Теперь все статусы корректно отображаются в столбце **Статус**, что позволяет правильно применять фильтр по статусам.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17625

2. Добавлены кнопки **Остановить все** и **Запустить все остановленные**. При нажатии **Остановить все** прекращается выполнение всех активных задач, а **Запустить все остановленные** инициирует возобновление работы всех приостановленных заданий.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/10190

3. Добавлена функция управления приоритетами проектов, также добавлены всплывающие подсказки для параметра **Приоритет**

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/7955

## Исправленные ошибки 

1. Изменен статус ошибки **Нехватка лицензий** на более понятный **Достигнуто максимальное количество работающих роботов на машине**
2. Исправлена ошибка в функции **Изменить статус в очереди**, которая нарушала ряд ограничений в таблицах `ExchangeQueueValueEvents` и `RpaProjectQueue`.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/11502   
https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/11501

3. Исправлена ошибка периодической блокировки учетной записи **RdpService**.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/11238

4. Исправлена ошибка взаимодействия агента с Оркестратором после обновления. Ранее ошибка в bat-файле при обработке аргумента (robotName) приводила к отправке запросов с пустым именем робота.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/11328

## Где найти
[Скачать дистрибутив Primo RPA Orchestrator](https://disk.primo-rpa.ru/index.php/s/primo?path=%2FRelease).

[Скачать дистрибутив Primo RPA Robot](https://disk.primo-rpa.ru/index.php/s/primo?path=%2FRelease%2FRobot%2FWindows):
* **Primo RPA Robot 1.24.4** — предназначен для установки на локальной рабочей станции. Выступает в роли цифрового ассистента пользователя. Дистрибутив поставляется в разрядности x64 и x86.
* **Primo RPA Robot Orchestrator 1.24.4** — предназначен для автоматической установки Оркестратором. Дистрибутив поставляется в разрядности x64 и x86.
