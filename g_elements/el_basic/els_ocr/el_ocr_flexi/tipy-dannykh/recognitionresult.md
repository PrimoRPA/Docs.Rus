# RecognitionResult

LTools.OCR.Model.FlexiCapture.RecognitionResult - результат обработки шаблона.
| Свойство             | Тип                                                      | Описание                                                     |
| -------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| \[string (имя поля)] | String                                                   | Данные поля                                                  |
| \[int (индекс)]      | KeyValuePair\<string, string>?                           | Данные поля, где ключ - это имя поля, а значение - его данные. Знак "?" в типе данных означает, что значение может быть null |
| Fields               | Dictionary\<string, string>                              | Массив полей. Ключ - имя поля, значение - его данные     |
| FieldBlocks          | Dictionary\<string, RecognitionBlock\>                   | Массив полей. Описание объекта **RecognitionBlock** приведено ниже  |
| Tables               | Disctionary\<string, List\<Dictionary\<string, string>>> | Массив таблиц (ключ - имя таблицы, значение - массив таблиц) |
| TableBlocks          | Dictionary\<string, RecognitionTable                     | Массив таблиц. Описание объекта **RecognitionTable** приведено ниже | 
| TemplateName         | String                                                   | Имя шаблона                                                  |
| State                | String                                                   | Статус результата обработки                                  |

## RecognitionBlock

LTools.OCR.Model.FlexiCapture.RecognitionBlock.

| Свойство                | Тип                           | Описание                      |
| ----------------------- | ----------------------------- | ----------------------------- |
| Key                     | String                        | Ключ                          |
| Text                    | String                        | Текст                         |
| Items                   | Dictionary\<string, string>   | Базовый элемент               |
| DKey                    | String                        | Ключ                          |
| Bounds                  | [Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=net-6.0) | Координаты  |
| HasSuspicious           | Boolean                       | Имеются подозрения            |

## RecognitionTable

LTools.OCR.Model.FlexiCapture.RecognitionTable.

| Свойство                | Тип                           | Описание                      |
| ----------------------- | ----------------------------- | ----------------------------- |
| Blocks                  | Dictionary<string, RecognitionBlock | Блоки                  |
| Bounds                  | [Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=net-6.0) | Координаты |




