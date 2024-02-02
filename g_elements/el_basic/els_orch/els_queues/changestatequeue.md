# Изменить статус в очереди

*Eng: Change queue item state*

Компонент позволяет изменить статус элемента [очереди обмена данных](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues) Оркестратора. Выбранный статус будет обозначать результат обработки элемента роботом. Например, присвоение статуса **Success** будет означать, что обработка элемента прошла успешно.

![](<../../../../.gitbook/assets/change-status-orch-queue-items.png>)

## Жизненный цикл элемента очереди

![](<../../../../.gitbook/assets1/items-states-diargam.png>)  

Статусы элемента: 
* **New** – элемент добавлен в очередь, но еще не извлечен ни одним роботом. 
* **InProgress** – робот извлек элемент из очереди (=занял). Другой робот не может обратиться к этому элементу.
* **Success** – обработка элемента завершена успешно, ошибок не обнаружено.
* **Error** – обработка элемента завершена с ошибкой общего вида. Например, робот не смог нажать определенную кнопку.
* **Business Error** – обработка элемента завершена с ошибкой в бизнес-логике.

Статусы **New** и **InProgress** являются логическими и вычисляются системой по косвенным признакам. В истории статусов в БД фиксируются только финальные статусы - **Success**, **Error**, **Business Error**.

### Как перевести элемент в InProgress

:small_orange_diamond: **Изменить статус в очереди** возможно только для элементов, которые находятся в **InProgress**. Если элемент находится в статусе **New**, изменить его состояние не получится.

Чтобы извлечь элемент из очереди используйте один из следующих компонентов:
* [Получить из очереди](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_orch/els\_queues/readfromqueue).
* [Получить из очереди по ID](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/peekqueueid) - требуется установить чекбокс **Занимать**, иначе элемент останется в статусе **New**.
* [Получить из очереди по фильтру](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/peekqueuefilter) - требуется установить чекбокс **Занимать**, иначе элемент останется в статусе **New**.


### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Очередь\*** *[String]* - название очереди Оркестратора, в которой находится элемент. Значение чувствительно к регистру. Пример: `"Queue name"`.
2. **ID\*** *[[Guid](https://learn.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-8.0&viewFallbackFrom=net-4.6.1)]* - идентификатор элемента очереди, указывается в виде переменной. Идентификатор можно получить и затем сохранить в переменную при чтении элемента. 
3. **Статус** - состояние обработки элемента. Выберите нужное значение в выпадающем списке: `Success` / `Error` / `Business Error`.
4. **Текст** *[String]* - комментарий к изменению статуса. Пример: `"Дополнительная информация от RPA-разработчика"`.
5. **Таймаут** *[Int32]* - лимит времени операции в миллисекундах. Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой. По умолчанию установлено `3000`.



### Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
