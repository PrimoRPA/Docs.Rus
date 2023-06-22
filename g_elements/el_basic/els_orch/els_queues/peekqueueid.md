# Получить из очереди по ID

![](<../../../../.gitbook/assets/получить из очереди по ID.png>)

Получает элементы очереди (значения) из Оркестратора по их ID.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

:small_blue_diamond: **Примечание**. Отличие между переменными вывода (Элемент, Таблица и Результат) заключается только в типе данных значения, вернувшегося из Оркестратора.

| Свойство   | Тип       | Описание                 | Пример
| ---------- | --------- | ------------------------ | ------------- |
| ***Процесс*** | | |
| Очередь\*  | String    | Название очереди в Оркестраторе | "Queue"
| ID\*       | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди Оркестратора, переменная | item_id
| Таймаут    | Int32     | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |
| Занимать   | Boolean   | По умолчанию флаг **НЕАКТИВЕН**. Определяет, нужно ли занимать отфильтрованные записи. Если установлен, то в ответе вернутся только те значения, которые можно сразу же занять - изъять из очереди, чтобы далее с ними работал ваш Робот   |
| ***Вывод*** | | |
| Элемент    | [LTools.Enterprise.Model.QueueItem](https://github.com/ttalantseva/Docs.Rus/blob/main/g_elements/el_basic/els_orch/els_queues/datatypes.md) | Переменная для хранения элемента очереди | item
| Таблица    | DataTable | Переменная для хранения полученных данных | item_table
| Результат  | String    | Переменная для хранения полученных данных | item_string

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

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
