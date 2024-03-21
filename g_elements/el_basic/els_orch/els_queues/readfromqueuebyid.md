---
description: Peek queue by ID
---

# Получить из очереди по ID

Компонент позволяет получить элемент [очереди обмена данными](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues) по его идентификатору (ID). Полученный из Оркестратора элемент сохраняется в переменную. Переменная может быть разных типов — строка, объект или DataTable. Выбор переменной осуществляется на ваше усмотрение.

Существует разница между «получением» элемента и его «извлечением» из очереди. При получении элемента его статус не меняется. При извлечении – другие роботы больше не смогут взять ваш элемент в работу. Только ваш робот будет иметь право изменять состояние извлеченного элемента или удалять его из очереди. Чтобы робот не просто получил, а извлек элемент из очереди, установите в свойствах компонента чекбокс **Занимать**. Извлекать возможно только элементы в статусе New. Подробнее о статусах элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues/items#statusy-elementa).

Перед началом работы с компонентом убедитесь, что настроена связь Студии и Оркестратора.

![](<../../../../.gitbook/assets/peek-queue-by-id.png>) 

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство   | Тип       | Описание                 | Пример
| ---------- | --------- | ------------------------ | ------------- |
| **Процесс:** | | |
| Очередь\*  | String    | Название очереди в Оркестраторе, чувствительно к регистру | `"Queue name"`
| ID\*       | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | ID элемента очереди Оркестратора, указывается в виде переменной | 
| Таймаут    | Int32     | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой | `5000`
| Занимать   | Boolean   | По умолчанию флаг **НЕАКТИВЕН**. Определяет, нужно ли занимать отфильтрованные записи. Если установлен, то в ответе вернутся только те значения, которые можно сразу же изъять из очереди, чтобы далее с ними работал ваш робот |
| **Вывод:** |   |   |
| Элемент    | [LTools.Enterprise.Model.QueueItem](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/datatypes) | Переменная для хранения элемента очереди в виде объекта | 
| Таблица    | [DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-8.0&viewFallbackFrom=net-4.6.1) | Переменная для хранения полученных данных в табличном виде | 
| Результат  | String    | Переменная для хранения полученных данных в строковом виде | 


## Только код
Ниже приведен пример использования элемента в процессе с типом **Только код** (Pure code):

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

## Дополнительно
* [Изменить статус в очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/changequeueitemstate) — присваивает элементу финальный статус обработки. 
* [Удалить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/deletefromqueue) — удаляет элемент из очереди.
