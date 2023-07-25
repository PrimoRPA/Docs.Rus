# Запустить робота

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (126).png>)

![](<../../../../.gitbook/assets/Запустить робота.png>)

Запускает Робота для выполнения задания в Оркестраторе. В свойствах нужно указать только название задания, Робот подберется автоматически.\
Используется для более быстрого выполнения нагруженных бизнес-процессов.

**ОБРАТИТЕ ВНИМАНИЕ!** Задание, которое указывается в свойствах, должно иметь тип триггера _Запуск из другого робота_. Подробнее о том, как настроить триггер, читайте в разделе [Задания](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks#vidy-triggerov).

| Свойство      | Тип    | Описание                                                                                                                      |
| ------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------- |
| _**Общие**_   |        | Описание общих свойств см. в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements) |
| _**Процесс**_ |        |                                                                                                                               |
| Задание\*     | String | Укажите имя задания, которое нужно запустить Роботом. Должно соответствовать имени задания в Оркестраторе                     |
| Таймаут       | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой                  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.InvokeRobot(wf, "name");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.InvokeRobot(wf, "name")
_lib.LTools.Enterprise.OrchestratorApp.InvokeRobot(wf, "name");
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
LTools.Enterprise.OrchestratorApp.InvokeRobot(wf, "name")
_lib.LTools.Enterprise.OrchestratorApp.InvokeRobot(wf, "name");
```
{% endtab %}
{% endtabs %}
