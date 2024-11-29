# InferenceResult

Свойства модели `Primo.AI.Server.Model.InferenceResult`:
- CreatedAt *[System.DateTime]* — дата создания OCR-запроса на инференс.
- ExpiresAt *[System.DateTime]* — дата завершения обработки документа.
- ModelType *[String]* — тип модели, который использовался для распознавания данных.
- ResultIsReady *[Boolean]* — флаг готовности результата: `true` (готов) или `false` (не готов).
- Result *[Primo.AI.Server.Model.InferenceResultContent]* — результат распознавания. 
- Files *[List\<Primo.AI.Server.Model.InferenceResultFile>]* — список обработанных файлов. 


## InferenceResultContent

Свойства модели `Primo.AI.Server.Model.InferenceResultContent`:
- CreatedAt *[System.DateTime]* — дата создания результата распознавания.
- ErrorMsg *[String]* — текст ошибки, если она присутствует. Например: `"Не запущены агенты для модели"`.
- Items *[List\<[Primo.AI.Server.Model.InferenceResultItem>]* — список распознанных элементов. 
- ThresholdOKMin *[String]* — порог, когда считается, что значение распозналось достоверно.
- ThresholdWarnMin *[String]* — порог, когда считается, что значение распозналось неоднозначно.
- ImageTransforms *[Primo.AI.Server.Model.ImageTransforms]* — преобразование изображения.

### InferenceResultItem

Свойства модели `Primo.AI.Server.Model.InferenceResultItem`:
- Field *[String]* — название поля.
- Text *[String]* — текст поля.
- ModelType *[String]* — тип модели (для классификации).
- Confidence *[Decimal]* — уверенность в корректности распознанных данных.
- Coordinates *[BoundingBox]* — координаты элемента, выделенного на изображении инструментом Add Bounding Box. 
- Rows *[List\<[Primo.AI.Server.Model.InferenceResultItemRow>]* — табличные данные, если они присутствуют в документе.


#### InferenceResultItemRow

Свойства модели `Primo.AI.Server.Model.InferenceResultItemRow`:
- Confidence *[Decimal]* — уверенность.
- Columns *[List<String>]* — список строк.


#### BoundingBox
Свойства модели `Primo.AI.Server.Model.BoundingBox`:
- MinX *[Decimal]* — минимальная координата X.
- MaxX *[Decimal]* — максимальная координата X.
- MinY *[Decimal]* — минимальная координата Y.
- MaxY *[Decimal]* — максимальная координата Y.

### ImageTransforms
Свойства модели `Primo.AI.Server.Model.ImageTransforms`:
- RotationAngle *[Decimal]* — угол поворота изображения.

