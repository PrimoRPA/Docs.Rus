# Получение из очереди по фильтру

Компонент, которые получает значения элементов из очереди Оркестратора по фильтру.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство   | Тип    | Описание                            | Пример
| ---------- | ------ | ----------------------------------- | --------- 
| Очередь\*  | String | Название очереди в Оркестраторе     | "Queque"
| ID\*       | String | ID элемента из очереди Оркестратора | queue_id.ToString()
| Фильтр     | String | Фильтр очереди (регулярное выражение) |
| Тэги       | List<string> | Фильтр по тегам элемента очереди |
| Статус     |        | Фильтр по статусу элемента очереди  |
| Занимать   |        | Занимать отфильтрованные записи     | 
| Страница   | Int32  | Номер страницы очереди Оркестратора, на которой находится искомый элемент |
| Кол-во     |        | Количество считываемых сообщений (элементов очереди). Определяет, нужно ли получить один элемент очереди или несколько |
| Только свои | Boolean | При установке флага будут прочитаны только те элементы очереди, которые были извлечены роботом |
| Логика     |        | Настраивает логику поиска тегов. Доступные значения: or или and. Если установлено or, то будет   | Or
| Элемент    | List<LTools.Enterprise.Model.QueueItem> | Список элементов очереди  |
| Результат  | String   | Переменная для хранения полученных данных | var1
  
  
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

