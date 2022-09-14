# Изменить статус в очереди

![](<../../../../.gitbook/assets/image (815).png>)

![](<../../../../.gitbook/assets/изменить статус в очереди.png>)

Позволяет изменить статус элемента очереди в Оркестраторе. Корректно работает после компонента [**Получить из очереди**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/readfromqueue).

В общем виде изменение статусов выглядит так:
1. Когда элемент добавляется в очередь Оркестратора, он получает статус *New*.
2. Когда элемент очереди был прочитан (см. **Получить из очереди**), он получает статус *Empty*.
3. Далее нужный статус присваивается в засимости от результата работы:    
    * Success - успешный, если не обнаружено ошибок.
    * Error - возникла системная ошибка, например, если робот не смог нажать кнопку.
    * Business Error - ошибка в бизнес-логике (в работе робота). 
    * Empty - при наличии расхождений в названии статусов импортированной очереди (например, из Blue Prism). Оригинальные статусы будут сохранены в метаданных.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство   | Тип    | Описание                 | Пример
| ---------- | :------: | ------------------------ | ----------------- 
| Очередь\*  | String | Название очереди Оркестратора, в которой находится элемент | "Queue"
| ID\*       | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди. Как правило, ID сохраняется в переменную при использовании до этого компонента **Получить из очереди** | queque_guid
| Статус     |    -   | Статус элемента. Выберите нужное значение в выпадающем списке   | Success
| Текст      | String | Комментарий к статусу    | "Доп.информация"


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.ChangeQueueItemState(wf, "queue", id, LTools.Enums.ExchangeQueueValueEventType.Success, "txt");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.ChangeQueueItemState(wf, "queue", id, LTools.Enums.ExchangeQueueValueEventType.Success, "txt")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Enterprise.OrchestratorApp.ChangeQueueItemState(wf, "queue", id, _lib.LTools.Enums.ExchangeQueueValueEventType.Success, "txt");
```
{% endtab %}
{% endtabs %}



