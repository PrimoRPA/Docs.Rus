# Запустить робота

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (126).png>)

![](<../../../../.gitbook/assets/Запустить робота.png>)

**Eng:** Invoke robot

Инициирует запуск робота для выполнения [задания](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks) в Оркестраторе. Помогает ускорить выполнение нагруженных бизнес-процессов.

Название задания указывается в свойствах элемента. Робот для указанного задания подберется автоматически.

:bangbang: ***Задание должно иметь тип триггера «Запуск из другого робота». Триггер выбирается в Оркестраторе, в настройках задания***.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство      | Тип    | Описание                                                                                                                      |
| ------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------- |
| _**Процесс:**_ |       |                                                                                                                              |
| Задание\*     | String | Укажите название задания, которое должен запустить робот. Должно соответствовать имени задания в Оркестраторе                 |
| Таймаут       | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой                  |

## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

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
