---
description: Get result
---


# Получить результат

Элемент получает от Primo RPA AI Server результат распознавания документа моделью нейронной сети. Результат сохраняется в переменную.

![](<../../../.gitbook/assets1/windows_items/WFPrimoAIGetInference.png>)


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
  
1. **Ключ запроса\*** *[System.Guid]* — ключ запроса.
1. **Результат** *[Primo.AI.Server.Model.InferenceResult]* — результат обработки документов.

## Описание модели InferenceResult

Свойства модели Primo.AI.Server.Model.InferenceResult:
- CreatedAt [System.DateTime]: Дата создания.
- ExpiresAt [System.DateTime]: Дата завершения.
- ModelType [String]: Тип модели.
- ResultIsReady [Boolean]: Флаг готовности результат.
- Result [Primo.AI.Server.Model.InferenceResultContent]: Результат.
- Files [List<Primo.AI.Server.Model.InferenceResultFile>]: Обработанные файлы.

Primo.AI.Server.Model.InferenceResultFile - Свойства:
  - OriginalFileName [String]: Наименование файла
  - ContentType [String]: Тип контента
  - ContentLength [Int64]: Длина контента

Primo.AI.Server.Model.InferenceResultContent - Свойства:
  - CreatedAt [System.DateTime]: Дата создания
  - ErrorMsg [String]: Текст ошибки
  - Items [List<Primo.AI.Server.Model.InferenceResultItem>]: Элементы

Primo.AI.Server.Model.InferenceResultItem - Свойства:
  - Field [String]: Имя поля
  - Text [String]: Текст поля
  - Confidence [Decimal]: Уверенность
  - Rows [List<Primo.AI.Server.Model.InferenceResultItemRow>]: Табличные данные

Primo.AI.Server.Model.InferenceResultItemRow - Свойства:
  - Confidence [Decimal]: Уверенность
  - Columns [List<String>]: Список строк
