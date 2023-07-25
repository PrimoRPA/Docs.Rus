# Удалить из очереди

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (8).png>)

![](<../../../../.gitbook/assets/удалить из очереди.png>)

Компонент, который удаляет элемент (значение) из очереди Оркестратора.

> Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство  | Тип                                                                          | Описание                                                                                                                                                                             | Пример       |
| --------- | ---------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------ |
| Очередь\* | String                                                                       | Название очереди в Оркестраторе                                                                                                                                                      | "Queque"     |
| ID\*      | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | Идентификатор элемента очереди (например, 9127dde8-dcb3-4406-931b-4066d09f1b04). Как правило, ID сохраняется в переменную при использовании ранее компонента **Получить из очереди** | queque\_guid |
| Таймаут   | Int32                                                                        | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой                                                                         |              |

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
