# Получение из очереди по фильтру

![](<../../../../.gitbook/assets/получить из очереди по фильтру.png>)

Компонент, который получает значения элементов из очереди Оркестратора по фильтру.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство   | Тип    | Описание                            | Пример
| ---------- | ------ | ----------------------------------- | --------- 
| Очередь\*  | String | Название очереди в Оркестраторе     | "Queque"
| ID         | String | ID элемента из очереди Оркестратора, переменная | queue_id.ToString()
| Фильтр     | String | Фильтр по очереди в виде регулярного выражения Excel | "%1330\|15.07.2022%"
| Тэги       | List\<string> | Фильтр по тегам элемента очереди | new List<string>( ) { "tag1", "tag2", "tag3" }
| Статус     |        | Фильтр по статусу элемента очереди. Выберите нужный из выпадающего списка  | Error
| Занимать   | Boolean | Нужно ли занимать отфильтрованные записи | 
| Страница   | Int32  | Номер страницы очереди Оркестратора, на которой находится искомый элемент | 5
| Кол-во     |        | Определяет, сколько элементов очереди нужно получить. Если не заполнено, вернется только 1 | 10
| Только свои | Boolean | При установке флага будут прочитаны только те сообщения, которые были добавлены в очередь с идентичной учетной записи (тем же роботом), с которой Вы осуществляете настройку |
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

