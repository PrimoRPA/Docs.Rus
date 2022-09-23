# RecognitionResult

LTools.OCR.Model.FlexiCapture.RecognitionResult

| Свойство             | Тип                                                      | Описание                                                     |
| -------------------- | -------------------------------------------------------- | ------------------------------------------------------------ |
| \[string (имя поля)] | String                                                   | Данные поля                                                  |
| \[int (индекс)]      | KeyValuePair\<string, string>?                           | Данные поля (ключ - имя поля, значение - данные поля)        |
| Fields               | Dictionary\<string, string>                              | Массив полей (ключ - имя поля, значение - значение поля)     |
| FieldBlocks          | Dictionary\<string, RecognitionBlock>                     | Массив полей                                                 |
| Tables               | Disctionary\<string, List\<Dictionary\<string, string>>> | Массив таблиц (ключ - имя таблицы, значение - массив таблиц) |
| TableBlocks          | Dictionary\<string, RecognitionTable>                     | Массив таблиц                                                | 
| TemplateName         | String                                                   | Имя шаблона                                                  |
| State                | String                                                   | Статус результата обработки                                  |
