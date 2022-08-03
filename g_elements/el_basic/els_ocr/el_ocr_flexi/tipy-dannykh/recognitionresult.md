# RecognitionResult

LTools.OCR.Model.FlexiCapture.RecognitionResult

| Свойство             | Тип                                                      | Описание                                                     |
| -------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| \[string (имя поля)] | string                                                   | Данные поля                                                  |
| \[int (индекс)]      | KeyValuePair\<string, string>?                           | Данные поля (ключ - имя поля, значение - данные поля)        |
| Fields               | Dictionary\<string, string>                              | Массив полей (ключ - имя поля, значение - значение поля)     |
| Tables               | Disctionary\<string, List\<Dictionary\<string, string>>> | Массив таблиц (ключ - имя таблицы, значение - массив таблиц) |
| TemplateName         | string                                                   | Имя шаблона                                                  |
| State                | string                                                   | Статус результата обработки                                  |
