---
description: Get result
---

# Получить результат

Элемент получает от Primo RPA AI Server результат обработки документа. Результат сохраняется в переменную, указанную пользователем в свойствах элемента.

![](<../../../.gitbook/assets1/windows_items/WFPrimoAIGetInference.png>)

## Перед началом работы

Установите в Студии библиотеку [Primo.AI.Server](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server), поскольку данный элемент входит в состав библиотеки.


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
  
1. **Ключ запроса\*** *[System.Guid]* — идентификатор запроса к Primo RPA AI Server. Получить его можно в результате выполнения элемента [Создать запрос](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/createrequest).
1. **Результат** *[Primo.AI.Server.Model.InferenceResult]* — название переменной, в которую сохранится результат обработки документа. Описание модели InferenceResult представлено ниже.


## Описание моделей

### InferenceResult

Свойства модели `Primo.AI.Server.Model.InferenceResult`:
- CreatedAt *[System.DateTime]* — дата создания запроса на инференс.
- ExpiresAt *[System.DateTime]* — дата завершения обработки документа.
- ModelType *[String]* — тип модели, который использовался для распознавания данных.
- ResultIsReady *[Boolean]* — флаг готовности результата: `true` (готов) или `false` (не готов).
- Result *[[Primo.AI.Server.Model.InferenceResultContent](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#inferenceresultcontent)]* — результат распознавания. 
- Files *[List\<[Primo.AI.Server.Model.InferenceResultFile](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#inferenceresultfile)>]* — список обработанных файлов. 


#### InferenceResultFile

Свойства модели `Primo.AI.Server.Model.InferenceResultFile`:
- OriginalFileName *[String]* — название обработанного файла.
- ContentType *[String]* — тип контента.
- ContentLength *[Int64]* — длина контента.

#### InferenceResultContent

Свойства модели `Primo.AI.Server.Model.InferenceResultContent`:
- CreatedAt *[System.DateTime]* — дата создания результата распознавания.
- ErrorMsg *[String]* — текст ошибки, если она присутствует. Например: `"Не запущены агенты для модели"`.
- Items *[List\<[Primo.AI.Server.Model.InferenceResultItem](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#inferenceresultitem)>]* — список распознанных элементов. 
- ThresholdOKMin *[String]* — порог, когда считается, что значение распозналось достоверно.
- ThresholdWarnMin *[String]* — порог, когда считается, что значение распозналось неоднозначно.
- ImageTransforms *[[Primo.AI.Server.Model.ImageTransforms](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#imagetransforms)]* — преобразование изображения.

#### InferenceResultItem

Свойства модели `Primo.AI.Server.Model.InferenceResultItem`:
- Field *[String]* — название поля.
- Text *[String]* — текст поля.
- ModelType *[String]* — тип модели (для классификации).
- Confidence *[Decimal]* — уверенность в корректности распознанных данных.
- Coordinates *[[BoundingBox](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#boundingbox)]* — координаты элемента, выделенного на изображении инструментом Add Bounding Box. 
- Rows *[List\<[Primo.AI.Server.Model.InferenceResultItemRow](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/getresult#inferenceresultitemrow)>]* — табличные данные, если они присутствуют в документе.

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

### ImageTransforms
Свойства модели `Primo.AI.Server.Model.ImageTransforms`:
- RotationAngle *[Decimal]* — угол поворота изображения.
