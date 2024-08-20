---
description: Get result
---

# Получить результат

Элемент получает от Primo RPA AI Server результат обработки документа ядром IDP. Результат сохраняется в переменную.

![](<../../../.gitbook/assets1/windows_items/WFPrimoAIGetInference.png>)

## Перед началом работы

Убедитесь, что в Студии установлена библиотека [Primo.AI.Server](https://github.com/PrimoRPA/Docs.Rus/tree/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server), поскольку данный элемент входит в состав библиотеки.


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
  
1. **Ключ запроса\*** *[System.Guid]* — идентификатор запроса к Primo RPA AI Server. Получить его можно в результате выполнения элемента [**Создать запрос**](https://github.com/PrimoRPA/Docs.Rus/blob/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server/createrequest.md).
1. **Результат** *[Primo.AI.Server.Model.InferenceResult]* — название переменной, в которую сохранится результат обработки документа. Описание модели InferenceResult представлено ниже.


## Описание моделей

### InferenceResult

Свойства модели `Primo.AI.Server.Model.InferenceResult`:
- CreatedAt *[System.DateTime]* — дата создания запроса на инференс.
- ExpiresAt *[System.DateTime]* — дата завершения обработки документа.
- ModelType *[String]* — тип модели, который использовался для распознавания данных.
- ResultIsReady *[Boolean]* — флаг готовности результата: `true` (готов) или `false` (не готов).
- Result *[Primo.AI.Server.Model.InferenceResultContent]* — результат распознавания. Описание модели InferenceResultContent приведено в подразделе ниже.
- Files *[List<Primo.AI.Server.Model.InferenceResultFile>]* — список обработанных файлов. Описание модели InferenceResultFile приведено ниже.


#### InferenceResultFile

Свойства модели `Primo.AI.Server.Model.InferenceResultFile`:
- OriginalFileName *[String]* — название обработанного файла.
- ContentType *[String]* — тип контента.
- ContentLength *[Int64]* — длина контента.

#### InferenceResultContent

Свойства модели `Primo.AI.Server.Model.InferenceResultContent`:
- CreatedAt *[System.DateTime]* — дата создания результата распознавания.
- ErrorMsg *[String]* — текст ошибки, если она присутствует. Например: `"Не запущены агенты для модели"`.
- Items *[List<Primo.AI.Server.Model.InferenceResultItem>]* — список распознанных элементов. Описание структуры элемента приведено ниже.
- ThresholdOKMin *[String]* — порог, когда считается, что значение распозналось достоверно.
- ThresholdWarnMin *[String]* — порог, когда считается, что значение распозналось неоднозначно.

#### InferenceResultItem

Свойства модели `Primo.AI.Server.Model.InferenceResultItem`:
- Field *[String]* — название поля.
- Text *[String]* — текст поля.
- ModelType *[String]* — тип модели (для классификации).
- Confidence *[Decimal]* — уверенность в корректности распознанных данных.
- Coordinates *[BoundingBox]* — координаты элемента, выделенного на изображении инструментом Add Bounding Box. Описание свойств модели BoundingBox приведено в подразделе ниже.
- Rows *[List<Primo.AI.Server.Model.InferenceResultItemRow>]* — табличные данные, если они присутствуют в документе.

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
