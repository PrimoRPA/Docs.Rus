# Оркестратор 1.24.6

История изменений в Primo RPA Orchestrator за июнь 2024-го года. 

## Обновления

3. Добавлена возможность конфигурировать параметр `SecureSocketOption` для почтовой рассылки в LTools.Orchestrator.Notifications. Данный параметр улучшает безопасность почтовых рассылок.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/18609



### Улучшения UX/UI

1. В разделе **Задания** исправлена ошибка, связанная с отображением и управлением заданий в статусе **Ошибка** (статус 4). Ранее задания в этом состоянии не позволяли использовать кнопки   **Запустить** и **Остановить**

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/19306

2. Устранена ошибка с выбором времени запуска в повторных расписаниях. Теперь при установке времени запуска в повторном расписании выпадающий список работает корректно.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/19054

3. 
## Улучшения в UI 3
1. Упрощено удаление элементов из очереди. Теперь элементы можно удалять прямо через меню **Действия** на странице Очереди без предварительного выбора чекбоксом. Ранее требовалось отдельное выделение каждого элемента.
   
https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/18627

2. Улучшено отображение графика:
- На вкладке **Очереди** теперь отображается количество удаленных элементов (`countRemoved`) под общим количеством через разделительную черту.
- Если значение `countRemoved` отсутствует, показывается график в стандартном виде.
- В форме редактирования очереди добавлена подсказка для поля `Физическое удаление`.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/18174

3. Добавлено отображение удаленных элементов в статистике очереди обмена данными.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17612

4. Изменено отображение параметра `Таймаут` в форме **Ресурсы**. Параметр указывается в секундах в формах добавления и редактирования.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17285

!!!5. Исправлена ошибка, из-за которой не отображалась информация в статистике очередей при создании большого количества очередей

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17181

6. Во вкладке Ресурсы в формах Добавить/Редактировать ресурс добавлены новые поля: `Тип внешнего хранилища` и `Учетная запись CyberArk`.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17162

## Исправленные ошибки
1. Исправлена ошибка запуска заданий. Ранее при попытке запустить задание, находящееся в статусе `Ошибка`, возвращалась `Команда Start не применима к заданию`. Теперь состояние задания корректно обновляется перед запуском, позволяя перевести задание в статус **Выполняется**

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/19450

2. Исправлена ошибка, при которой робот в Оркестраторе оставался в статусе `Завершается работа` после выполнения проекта.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17429

!!!3. Исправлена ошибка, при котором запросы в журнал робота по ID шли без даты по всем секциям. Теперь к запросу добавлен дополнительный параметр operationKey, поддерживаемый в UI2 и UI3.

https://azure-dos.s1.primo1.orch/PrimoCollection/Orchestrator/_workitems/edit/17271



## Где найти
[Скачать комплект поставки Оркестратора:](https://disk.primo-rpa.ru/index.php/s/primo?path=%2FRelease%2FOrchestrator)
* **Primo RPA Orchestrator 1.24.2 FULL.zip** — полный комплект поставки, в который входят дистрибутивы Оркестратора и внешних компонентов: например, базы данных PostgreSQL Server, брокера сообщений RabbitMQ и др. 
* **Primo RPA Orchestrator 1.24.2.zip** — облегченный вариант поставки.

[Скачать дистрибутив Robot Enterprise](https://disk.primo-rpa.ru/index.php/s/primo?path=%2FRelease%2FRobot). Архив должен иметь название **Primo RPA Robot Orchestrator <архитектура> 1.24.2.zip**. Дистрибутив этого робота загружается непосредственно в Оркестратор.
