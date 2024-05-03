---
description: Delete from queue
---

# Удалить из очереди

Компонент позволяет удалить элемент из [очереди обмена данных](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues) Оркестратора. Если указанный элемент очереди был извлечен роботом, то удалить этот элемент сможет только тот робот, который его извлек.

![Элемент «Удалить из очереди»](<../../../../.gitbook/assets/delete-orch-queue-item-by-studio.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство  | Тип                                                                          | Описание                                                                                                           | Пример       |
| --------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------ |
| Очередь\* | String                                                                       | Название очереди в Оркестраторе. Чувствительно к регистру                                                          | `"Queque_name"`|
| ID\*      | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | Автоматический идентификатор элемента очереди (например, 9127dde8-dcb3-4406-931b-4066d09f1b04). Как правило, указывается в виде переменной |     |
| Таймаут   | Int32                                                                        | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой       | `3000`       |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.DeleteQueueItem(wf, "queue", id);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.DeleteQueueItem(wf, "queue", id)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Enterprise.OrchestratorApp.DeleteQueueItem(wf, "queue", id);
```
{% endtab %}
{% endtabs %}
