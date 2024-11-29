# NlpResultContent

Свойства модели `Primo.AI.Server.Model.NlpResultContent`:
1. **StreamingStartedAt** *[System.DateTimeOffset]* — дата и время получения первого фрагмента результата.
1. **UpdatedAt** *[System.DateTimeOffset]* — дата и время последнего обновления ответа.
1. **StreamingCompletedAt** *[System.DateTimeOffset]* — дата и время завершения генерации результата.
1. **IsReady** *[System.Boolean]* — флаг готовности результата: `true`— готов / `false` — не готов.
1. **IsFailed** *[System.Boolean]* — флаг ошибочной обработки запроса.
1. **Answer** *[String]* — текст ответа.
1. **ErrorMsg** *[String]* — текст ошибки.
