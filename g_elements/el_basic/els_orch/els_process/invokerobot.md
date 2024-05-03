---
description: Invoke robot
---


# Запустить робота

Элемент инициирует запуск робота для выполнения [задания](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks) в Оркестраторе. Это помогает ускорить выполнение нагруженных бизнес-процессов.

Задание, которое вы хотите выполнить, должно иметь тип триггера [«Запуск из другого робота»](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks#id-6.-zapusk-iz-drugogo-robota). Робот для указанного задания подберется автоматически.

![Элемент «Запустить робота»](<../../../../.gitbook/assets/Запустить робота.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство      | Тип    | Описание                                                                                                                      |
| ------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **Процесс:**  |        |                                                                                                                               |
| Задание\*     | String | Название задания в Оркестраторе, которое вы хотите запустить. Соблюдайте регистр      |
| Таймаут       | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой. По умолчанию `5000` |

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
