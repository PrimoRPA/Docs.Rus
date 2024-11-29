# InferenceResultItem

Свойства модели `Primo.AI.Server.Model.InferenceResultItem`:
- Field *[String]* — название поля.
- Text *[String]* — текст поля.
- ModelType *[String]* — тип модели (для классификации).
- Confidence *[Decimal]* — уверенность в корректности распознанных данных.
- Coordinates *[BoundingBox]* — координаты элемента, выделенного на изображении инструментом Add Bounding Box. 
- Rows *[List\<[Primo.AI.Server.Model.InferenceResultItemRow>]* — табличные данные, если они присутствуют в документе.


### InferenceResultItemRow

Свойства модели `Primo.AI.Server.Model.InferenceResultItemRow`:
- Confidence *[Decimal]* — уверенность.
- Columns *[List<String>]* — список строк.


### BoundingBox
Свойства модели `Primo.AI.Server.Model.BoundingBox`:
- MinX *[Decimal]* — минимальная координата X.
- MaxX *[Decimal]* — максимальная координата X.
- MinY *[Decimal]* — минимальная координата Y.
- MaxY *[Decimal]* — максимальная координата Y.

