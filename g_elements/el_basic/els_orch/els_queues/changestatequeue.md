# Изменить статус в очереди

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (72).png>)

![](<../../../../.gitbook/assets/изменить статус в очереди.png>)

Позволяет изменить статус элемента очереди в Оркестраторе. Корректно работает после компонента [**Получить из очереди**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_orch/els\_queues/readfromqueue).

В общем виде изменение статусов выглядит так:

1. Когда элемент добавляется в очередь Оркестратора, он автоматически получает статус _New_.
2. Когда элемент очереди был прочитан (см. **Получить из очереди**), он автоматически получает статус _Empty_.
3. Далее нужный статус присваивается разработчиком с помощью компонента **Изменить статус в очереди**. Статус выбирается в засимости от результата работы:
   * Success - успешный, если не обнаружено ошибок.
   * Error - возникла системная ошибка, например, если Робот не смог нажать кнопку.
   * Business Error - ошибка в бизнес-логике (в работе Робота).
   * Empty - при наличии расхождений в названии статусов импортированной очереди (например, из Blue Prism). Оригинальные статусы будут сохранены в метаданных.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство  |     Тип                                | Описание                          | Пример           |
| --------- | :------------------------------------: | --------------------------------- | ---------------- |
| Очередь\* |  String                                    | Название очереди Оркестратора, в которой находится элемент  | "Queue" |
| ID\*      | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди. Как правило, ID сохраняется в переменную при использовании до этого компонента **Получить из очереди** | queque\_guid     |
| Статус    | -                                      | Статус элемента. Выберите нужное значение в выпадающем списке | Success  |
| Текст     | String                                 | Комментарий к статусу  | "Доп.информация" |
| Таймаут   | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой | 3000 |

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
