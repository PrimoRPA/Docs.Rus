# Получить из очереди по ID

*Eng: Peek queue by ID*

Компонент позволяет получить элемент очереди Оркестратора по его идентификатору (ID). Для успешной работы должна быть настроена связь Студии и Оркестратора.

![](<../../../../.gitbook/assets/peek-queue-by-id.png>) 

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения.\
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

:small_blue_diamond: **Примечание**. Отличие между свойствами вывода (Элемент, Таблица, Результат) заключается только в типе данных.

| Свойство   | Тип       | Описание                 | Пример
| ---------- | --------- | ------------------------ | ------------- |
| ***Процесс:*** | | |
| Очередь\*  | String    | Название очереди в Оркестраторе, чувствительно к регистру | `"Queue name"`
| ID\*       | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди Оркестратора, переменная | `item_guid`
| Таймаут    | Int32     | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой | `5000`
| Занимать   | Boolean   | По умолчанию флаг **НЕАКТИВЕН**. Определяет, нужно ли занимать отфильтрованные записи. Если установлен, то в ответе вернутся только те значения, которые можно сразу же изъять из очереди, чтобы далее с ними работал ваш робот |
| ***Вывод:*** |   |   |
| Элемент    | [LTools.Enterprise.Model.QueueItem](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/datatypes) | Переменная для хранения элемента очереди | `item`
| Таблица    | DataTable | Переменная для хранения полученных данных в табличном виде | `item_table`
| Результат  | String    | Переменная для хранения полученных данных в строковом виде | `item_string`

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
