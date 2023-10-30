# Удалить из очереди

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (8).png>)

![](<../../../../.gitbook/assets/delete-orch-queue-item-by-studio.png>)

**«Удалить из очереди» (Delete from queue)** - позволяет удалить элемент из очереди Оркестратора.

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство  | Тип                                                                          | Описание                                                                                                           | Пример       |
| --------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------ | ------------ |
| Очередь\* | String                                                                       | Название очереди в Оркестраторе. Чувствительно к регистру                                                          | `"Queque name"`|
| ID\*      | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | Идентификатор элемента очереди (например, 9127dde8-dcb3-4406-931b-4066d09f1b04). Как правило, указывается в виде переменной  | `queque_guid` |
| Таймаут   | Int32                                                                        | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой                 |               |

### Только код
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
