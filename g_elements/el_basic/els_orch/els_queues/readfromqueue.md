# Получить из очереди

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (107).png>)

![](<../../../../.gitbook/assets/image (393).png>)

Компонент, производящий получение значения из очереди Оркестратора. В ответе вернется первый элемент очереди.

**Примечание**. Отличие между свойствами вывода *Элемент, Таблица и Результат* заключается только в типе данных, в котором значение вернулось из Оркестратора.

| Свойство  | Тип    | Описание                                  |
| --------- | ------ | ----------------------------------------- |
| ***Процесс*** |   |  
| Очередь\* | String | Имя очереди                               |
| Статус    | LTools.Enterprise.Model.QueueItemStates | Состояние элемента: New, Error, Repeated Error |   
| Таймаут   | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |
| ***Вывод*** |     |    |
| Результат | String | Переменная для хранения полученных данных |
| Элемент    | [LTools.Enterprise.Model.QueueItem](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/datatypes) | Переменная для хранения элемента очереди в виде объекта | 
| Таблица    | DataTable | Переменная для хранения полученных данных в виде таблицы | 


{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "queue");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "queue")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "queue");
```
{% endtab %}
{% endtabs %}
