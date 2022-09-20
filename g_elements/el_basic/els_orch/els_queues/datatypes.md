# Типы данных

## QueueItem

Объект LTools.Enterprise.Model.QueueItem описывает структуру элемента, который находится в очереди Оркестратора.


| Свойство    | Тип                                                             | Описание             | 
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | [Guid](https://docs.microsoft.com/ru-ru/dotnet/api/system.guid?view=net-6.0) | Идентификатор элемента очереди. Присваивается автоматически. Например, 9127dde8-dcb3-4406-931b-4066d09f1b04
| Key         | String                                                          | Ключ элемента очереди
| Data        | Object                                                          | Данные, которые содержит элемент (то же, что и **Значение** в интерфейсе очередей Оркестратора) 
| Table       | [System.Data.DataTable](https://docs.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0) | Данные элемента, представленные в виде таблицы 
| Metadata    | Dictionary\<string, string>                                     | Дополнительные сведения об элементе | 
| Tags        | List\<string>                                                   | Теги элемента |
| QueueName   | String                                                          | Название очереди в Оркестраторе, в которой находится данный элемент |
| PostponeAt  | [DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=net-6.0) | Время, до которого откладывается обработка значения элемента. Например: dd.MM.yyyy HH:mm:ss |
| DeadlineAt  | DateTime                                                        | Время, после которого элемент будет удален из очереди |
| State       | Ltools.Enums.ExchangeQueueValueEventType2?                      | Состояние обработки элемента очереди.  |

