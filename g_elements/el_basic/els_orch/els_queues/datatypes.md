# Типы данных

## QueueItem

Объект LTools.Enterprise.Model.QueueItem описывает структуру элемента, который находится в очереди Оркестратора.


| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | Идентификатор элемента очереди |
| Key         | String                                                          | Ключ элемента очереди |
| Metadata    | Dictionary\<string, string>                                     | Метаданные элемента очереди |
| Tags        | List\<string>                                                   | Теги элемента         |
| QueueName   | String                                                          | Название очереди в Оркестраторе |
| Data        | Object                                                          | Данные элемента |
| Table       | [System.Data.DataTable](https://docs.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0) | Данные элемента, представленные в виде таблицы |
| PostponeAt  | DateTime?                                                       | Время, до которого откладывается обработка значения элемента |
| DeadlineAt  | DateTime?                                                       | Время, после которого элемент удаляется из очереди |
| State       | Ltools.Enums.ExchangeQueueValueEventType2?                      | Статус, в котором находится элемент |

