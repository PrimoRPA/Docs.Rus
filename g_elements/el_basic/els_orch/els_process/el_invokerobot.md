# Запустить робота

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (153).png>)

![](<../../../../.gitbook/assets/Запустить робота.png>)

Элемент запускает Робота для выполнения задания в Оркестраторе. В свойствах нужно указать только название задания, Робот подберется автоматически.\
Используется для более быстрого выполнения нагруженных бизнес-процессов.

**ОБРАТИТЕ ВНИМАНИЕ!** Задание, которое указывается в свойствах, должно иметь тип триггера **Запуск из другого робота**.
Подробнее о том, как настроить триггер, читайте в разделе [Задания](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks#vidy-triggerov).

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*.

| Свойство    | Тип     | Описание                                  |
| ----------- | ------- | ----------------------------------------- |
| Задание\*   | String  | Укажите имя задания, которое нужно запустить Роботом. Оно должно соответствовать имени задания в Оркестраторе |

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
