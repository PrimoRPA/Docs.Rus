# Типы данных

## QueueItem

Объект LTools.Enterprise.Model.QueueItem описывает структуру элемента, который находится в очереди Оркестратора.


| Свойство    | Тип                                                             | Описание             | 
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | Идентификатор элемента очереди. Присваивается автоматически. Например, 9127dde8-dcb3-4406-931b-4066d09f1b04
| Key         | String                                                          | Ключ элемента очереди. В отличие от ID ключ можно присвоить вручную, например, при использовании элемента Студии [**Добавить в очередь**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/addtoqueue). В очереди Оркестратора он будет доступен в поле **Натуральный ключ**
| Data        | Object                                                          | Данные, которые содержит элемент (то же, что и **Значение** в интерфейсе очередей Оркестратора) 
| Table       | [System.Data.DataTable](https://docs.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0) | Также данные элемента, но представленные в виде таблицы 
| Metadata    | Dictionary\<string, string>                                     | Дополнительные сведения об элементе. Помогают при фильтрации элементов | 
| Tags        | List\<string>                                                   | Теги элемента. Помогают при фильтрации элементов |
| QueueName   | String                                                          | Название очереди в Оркестраторе, в которой находится данный элемент |
| PostponeAt  | [DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=net-6.0) | Время, до которого откладывается обработка значения элемента |
| DeadlineAt  | DateTime                                                        | Время, после которого элемент будет удален из очереди |
| State       | Ltools.Enums.ExchangeQueueValueEventType2                       | Состояние обработки элемента очереди. Возможные статусы: New, Empty, Success, Error, Business Error. Подробнее описаны в [этом разделе](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/orkestrator/els_queues/changestatequeue) |
| StateText   | String                                                          | Содержит комментарий, добавленный при изменении статуса элемента очереди |
