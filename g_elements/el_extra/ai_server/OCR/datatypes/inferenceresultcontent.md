# InferenceResultContent

Свойства модели `Primo.AI.Server.Model.InferenceResultContent`:
- CreatedAt *[System.DateTime]* — дата создания результата распознавания.
- ErrorMsg *[String]* — текст ошибки, если она присутствует. Например: `"Не запущены агенты для модели"`.
- Items *[List\<[Primo.AI.Server.Model.InferenceResultItem>]* — список распознанных элементов. 
- ThresholdOKMin *[String]* — порог, когда считается, что значение распозналось достоверно.
- ThresholdWarnMin *[String]* — порог, когда считается, что значение распозналось неоднозначно.
- ImageTransforms *[Primo.AI.Server.Model.ImageTransforms]* — преобразование изображения.



