# Получить результат NLP

Элемент получает результат NLP-запроса от Primo AI Server.




Свойства
  - Ключ запроса*: [System.Guid] Ключ запроса
  - Результат: [Primo.AI.Server.Model.NlpResult] Результат запроса

Primo.AI.Server.Model.NlpResult - Свойства:
  - CreatedAt [System.DateTimeOffset]: Дата создания запроса
  - ExpiresAt [System.DateTimeOffset]: Дата, до которой хранятся все данные запроса
  - RoutingKey [String]: Ключ маршрутизации
  - Key [Guid]: Ключ запроса
  - Result [Primo.AI.Server.Model.NlpResultContent]: Результат

Primo.AI.Server.Model.NlpResultContent - Свойства:
  - StreamingStartedAt [System.DateTimeOffset]: Дата и время получения первого фрагмента результата
  - UpdatedAt [System.DateTimeOffset]: Дата и время последнего обновления ответа
  - StreamingCompletedAt [System.DateTimeOffset]: Дата и время завершения генерации результата
  - IsReady [System.DateTime]: Флаг готовности результата
  - IsFailed [String]: Флаг ошибочной обработки запроса
  - Answer [String]: Текст ответа
  - ErrorMsg [String]: Текст ошибки
