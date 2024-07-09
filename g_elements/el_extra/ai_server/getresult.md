---
description: Get result
---

# Получить результат

Элемент получает от Primo RPA AI Server результат распознавания документа моделью нейронной сети. Результат сохраняется в переменную.

![](<../../../.gitbook/assets1/windows_items/WFPrimoAIGetInference.png>)


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
  
1. **Ключ запроса\*** *[System.Guid]* — ключ запроса. Ключом является результат выполнения элемента [**Создать запрос**](https://github.com/PrimoRPA/Docs.Rus/blob/1299-%D0%BD%D0%B0%D0%BF%D0%B8%D1%81%D0%B0%D1%82%D1%8C-%D0%B4%D0%BE%D0%BA%D1%83%D0%BC%D0%B5%D0%BD%D1%82-%D0%BF%D0%BE-primoai/g_elements/el_extra/ai_server/createrequest.md), сохраненный в переменную.
1. **Результат** *[Primo.AI.Server.Model.InferenceResult]* — название переменной для сохранения результата обработки документов. Описание модели InferenceResult представлено ниже.


## Описание моделей

### InferenceResult

Свойства модели Primo.AI.Server.Model.InferenceResult:
- CreatedAt *[System.DateTime]* — дата создания.
- ExpiresAt *[System.DateTime]* — дата завершения.
- ModelType *[String]* — тип модели.
- ResultIsReady *[Boolean]* — флаг готовности результат.
- Result *[Primo.AI.Server.Model.InferenceResultContent]* — результат.
- Files *[List<Primo.AI.Server.Model.InferenceResultFile>]* — обработанные файлы.


### InferenceResultFile

Свойства модели Primo.AI.Server.Model.InferenceResultFile:
- OriginalFileName *[String]* — наименование файла.
- ContentType *[String]* — тип контента.
- ContentLength *[Int64]* — длина контента.

### InferenceResultContent

Свойства модели Primo.AI.Server.Model.InferenceResultContent:
- CreatedAt *[System.DateTime]* — дата создания.
- ErrorMsg *[String]* — текст ошибки.
- Items *[List<Primo.AI.Server.Model.InferenceResultItem>]* — элементы.

### InferenceResultItem

Свойства модели Primo.AI.Server.Model.InferenceResultItem:
- Field *[String]* — имя поля.
- Text *[String]* — текст поля.
- Confidence *[Decimal]* — уверенность.
- Rows *[List<Primo.AI.Server.Model.InferenceResultItemRow>]* — табличные данные.

### InferenceResultItemRow

Свойства модели Primo.AI.Server.Model.InferenceResultItemRow:
- Confidence *[Decimal]* — уверенность.
- Columns *[List<String>]* — список строк.
