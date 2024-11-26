# NlpResult

Primo.AI.Server.Model.NlpResult — результат обработки NLP-запроса, полученный от Primo RPA AI Server.

Свойства:
1. **CreatedAt** *[System.DateTimeOffset]* — дата создания запроса.
1. **ExpiresAt** *[System.DateTimeOffset]* — дата, до которой хранятся все данные запроса.
1. **RoutingKey** *[String]* — ключ маршрутизации запроса.
1. **Key** *[Guid]* — идентификатор запроса.
1. **Result** *[Primo.AI.Server.Model.NlpResultContent]* — результат выполнения запроса.


## NlpResultContent

Primo.AI.Server.Model.NlpResultContent.

Свойства:
1. **StreamingStartedAt** *[System.DateTimeOffset]* — дата и время получения первого фрагмента результата.
1. **UpdatedAt** *[System.DateTimeOffset]* — дата и время последнего обновления ответа.
1. **StreamingCompletedAt** *[System.DateTimeOffset]* — дата и время завершения генерации результата.
1. **IsReady** *[System.DateTime]* — флаг готовности результата.
1. **IsFailed** *[String]* — флаг ошибочной обработки запроса.
1. **Answer** *[String]* — текст ответа.
1. **ErrorMsg** *[String]* — текст ошибки.



