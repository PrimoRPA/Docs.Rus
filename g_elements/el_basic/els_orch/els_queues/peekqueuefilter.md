# Получение из очереди по фильтру

![](<../../../../.gitbook/assets/получить из очереди по фильтру.png>)

Компонент, которые получает значения элементов из очереди Оркестратора по фильтру.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство   | Тип    | Описание                            | Пример
| ---------- | ------ | ----------------------------------- | --------- 
| Очередь\*  | String | Название очереди в Оркестраторе     | "Queque"
| ID\*       | String | ID элемента из очереди Оркестратора, переменная | queue_id.ToString()
| Фильтр     | String | Фильтр очереди (регулярное выражение). Используется регулярное выражение Excel | "%1330\|15.07.2022%"
| Тэги       | List\<String> | Фильтр по тегам элемента очереди | 
| Статус     |        | Фильтр по статусу элемента очереди  |
| Занимать   |        | Занимать отфильтрованные записи     | 
| Страница   | Int32  | Номер страницы очереди Оркестратора, на которой находится искомый элемент | 5
| Кол-во     |        | Количество считываемых сообщений (элементов очереди). Определяет, сколько элементов нужно получить | 1
| Только свои | Boolean | При установке флага будут прочитаны только те элементы очереди, которые были извлечены роботом |
| Логика     |        | Настраивает логику поиска тегов. Доступные значения: *Or* или *And*. Если установлено *Or*, то будет учитываться один и более тегов. Если установлено *And*, то у элемента должны быть все перечисленные теги | Or
| Элемент    | List<LTools.Enterprise.Model.QueueItem> | Список [элементов очереди](https://github.com/ttalantseva/Docs.Rus/blob/main/g_elements/el_basic/els_orch/els_queues/datatypes.md)  |
| Результат  | String   | Переменная для хранения полученных данных | item_1
  
  
{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.PeekQueueByFilter(wf, "queue", id, ".name", LTools.Enterprise.Model.QueueItemStates2.Any, false, 10);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.PeekQueueByFilter(wf, "queue", id, ".name", LTools.Enterprise.Model.QueueItemStates2.Any, false, 10)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.PeekQueueByFilter(wf, "queue", id, ".name", _lib.LTools.Enterprise.Model.QueueItemStates2.Any, false, 10);
```
{% endtab %}
{% endtabs %}

