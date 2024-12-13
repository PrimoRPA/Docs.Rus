# InferenceResult

Свойства модели `Primo.AI.Server.Model.InferenceResult`:
- CreatedAt *[System.DateTime]* — дата создания OCR-запроса на инференс.
- ExpiresAt *[System.DateTime]* — дата завершения обработки документа.
- ModelType *[String]* — тип модели, который использовался для распознавания данных.
- ResultIsReady *[Boolean]* — флаг готовности результата: `true` (готов) или `false` (не готов).
- Result *[Primo.AI.Server.Model.InferenceResultContent]* — результат распознавания. 
- Files *[List\<Primo.AI.Server.Model.InferenceResultFile>]* — список обработанных файлов. 


