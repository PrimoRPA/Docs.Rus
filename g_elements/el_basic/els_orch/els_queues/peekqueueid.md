# Получить из очереди по ID

![](<../../../../.gitbook/assets/получить из очереди по ID.png>)

Получает элементы (значения) из очереди Оркестратора по ID.

> ***Примечание**. Отличие между свойствами вывода Элемент, Таблица и Результат заключается только в типе данных, в котором значение вернулось из Оркестратора.*

| Свойство   | Тип    | Описание                 | Пример
| ---------- | ------ | ------------------------ | ------------- |
| ***Процесс*** |   |    |
| Очередь\*  | String | Название очереди в Оркестраторе | "Queue"
| ID\*       | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди Оркестратора, переменная | item_id
| Таймаут   | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |
| ***Вывод*** |   |   |
| Элемент    | [LTools.Enterprise.Model.QueueItem](https://github.com/ttalantseva/Docs.Rus/blob/main/g_elements/el_basic/els_orch/els_queues/datatypes.md) | Переменная для хранения элемента очереди | item
| Таблица    | DataTable | Переменная для хранения полученных данных | item_table
| Результат  | String    | Переменная для хранения полученных данных | item_string


{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.PeekQueueById(wf, "queue", id, false);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.PeekQueueById(wf, "queue", id, false)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.PeekQueueById(wf, "queue", id, false);
```
{% endtab %}
{% endtabs %}
