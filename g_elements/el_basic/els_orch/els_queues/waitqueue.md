---
description: Wait queue
---

# Ожидать сообщения из очереди

Компонент ожидает появление нового элемента в [очереди обмена данных](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues). При появлении элемента, робот извлечет его из очереди Оркестратора и сохранит в переменную. Извлеченный элемент перейдет из состояния New в InProgress. Это означает, что он будет доступен вашему роботу для дальнейшей обработки в рамках сценария автоматизации. Подробнее о статусах элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/data-queues/items#statusy-elementa).

Если во время выполнения компонента очередь окажется пустой, то робот будет опрашивать очередь в течение заданного времени из свойства **Time**. Это отличает данный компонент от других способов извлечения элемента, например, от [**Получить из очереди**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/readfromqueue).  

![Элемент «Ожидать сообщения из очереди»](<../../../../.gitbook/assets/ожидать сообщения из очереди.png>)


### Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

> *Переменная, в которую будет записан элемент, может быть  в виде объекта, DataTable или строки. Выбор переменной осуществляется на ваше усмотрение.*

| Свойство      | Тип                                                                                                                                      | Описание                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------- |
| **Процесс:**  |                                                                                                                                          |                                                                                  |
| Очередь\*     | String                                                                                                                                   | Название очереди в Оркестраторе. Пример: `"PrimoTestQueue"`                      |
| **Прочее:**   |                                                                                                                                          |                                                                                  |
| Time          | Int32                                                                                                                                    | Период опроса очереди в миллисекундах. По умолчанию `1000`                       |
| **Вывод:**    |                                                                                                                                          |                                                                                  |
| Таблица       | [DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-8.0&viewFallbackFrom=net-4.6.1)                  | Название переменной, которая будет хранить полученный элемент очереди в виде таблицы |
| Результат     | String                                                                                                                                   | Название переменной, которая будет хранить полученный элемент очереди в виде строки  |
| Элемент       | [LTools.Enterprise.Model.QueueItem](https://docs.primo-rpa.ru/primo-rpa/g\_elements/osnovnye-elementy/orkestrator/els\_queues/datatypes) | Название переменной, которая будет хранить полученный элемент очереди в виде объекта |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//wf: [LTools.Common.Model.WorkflowData] ссылка на вызывающий алгоритм
//queue - Очередь: [String] Имя очереди
//robot - Статус элемента
object ret = LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "PrimoTestQueue", LTools.Enterprise.Model.QueueItemStates.Any);
		
//Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, "Полученное значение из очереди - " + ret.ToString(), LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#wf: [LTools.Common.Model.WorkflowData] - Ссылка на вызывающий алгоритм
#queue - Очередь: [String] Имя очереди
#robot - Статус элемента
ret = LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "PrimoTestQueue", LTools.Enterprise.Model.QueueItemStates.Any)
		
#Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, "Полученное значение из очереди - " + str(ret), LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//wf: [LTools.Common.Model.WorkflowData] - Ссылка на вызывающий алгоритм
//queue - Queue: [String] Имя очереди
//robot - Статус элемента
let ret = _lib.LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "PrimoTestQueue", _lib.LTools.Enterprise.Model.QueueItemStates.Any);
		
//Вывод в лог	
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, "Полученное значение из очереди - " + ret.toString(), _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}

## Дополнительно
* [Изменить статус в очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/changequeueitemstate) — присваивает элементу финальный статус обработки. 
* [Удалить из очереди](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_queues/deletefromqueue) — удаляет элемент из очереди.
