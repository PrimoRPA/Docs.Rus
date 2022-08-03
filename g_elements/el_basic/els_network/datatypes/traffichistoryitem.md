# TrafficHistoryItem

LTools.Network.Model.TrafficHistoryItem

| Свойство    | Тип                                                                           | Описание                              |
| ----------- | ----------------------------------------------------------------------------- | ------------------------------------- |
| ID          | String                                                                        | Идентификатор запроса                 |
| Name        | String                                                                        | Наименование запроса                  |
| URL         | String                                                                        | URL Web-сервиса                       |
| Method      | String                                                                        | Web-метод (POST)                      |
| ContentType | String                                                                        | Тип контента (application/json)       |
| Headers     | ObservableCollection <[LTools.Network.Model.PackageHeader](packageheader.md)> | Массив заголовков запроса Web-сервиса |
| Body        | String                                                                        | Тело запроса Web-сервиса              |

