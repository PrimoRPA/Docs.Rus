# Получить из очереди по ID

Получает элементы (значения) из очереди Оркестратора по ID.

> *Отличие между свойствами вывода Элемент, Таблица и Результат заключается только в типе данных, в котором значение вернулось из Оркестратора*

| Свойство   | Тип    | Описание                 | Пример
| ---------- | ------ | ------------------------ | -------------
| Очередь\*  | String | Название очереди в Оркестраторе | "Queue"
| ID\*       | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди Оркестратора | 9127dde8-dcb3-4406-931b-4066d09f1b04
| Элемент    | [LTools.Enterprise.Model.QueueItem](https://github.com/ttalantseva/Docs.Rus/blob/main/g_elements/el_basic/els_orch/els_queues/datatypes.md) | Переменная для хранения элемента очереди | 
| Таблица    | DataTable | Переменная для хранения полученных данных | 
| Результат  | String    | Переменная для хранения полученных данных | 


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
