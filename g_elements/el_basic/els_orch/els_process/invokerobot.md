---
description: Invoke robot
---


# Запустить робота

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (126).png>)

![](<../../../../.gitbook/assets/Запустить робота.png>)

Элемент инициирует запуск робота для выполнения [задания](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks) в Оркестраторе. Помогает ускорить выполнение нагруженных бизнес-процессов.

Задание должно иметь тип триггера [«Запуск из другого робота»](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks#id-6.-zapusk-iz-drugogo-robota). Название задания указывается в свойствах элемента. Робот для указанного задания подбирается автоматически.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство      | Тип    | Описание                                                                                                                      |
| ------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------- |
| **Процесс:**  |        |                                                                                                                                |
| Задание\*     | String | Название задания, которое должен запустить робот. Должно соответствовать имени задания в Оркестраторе                 |
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
