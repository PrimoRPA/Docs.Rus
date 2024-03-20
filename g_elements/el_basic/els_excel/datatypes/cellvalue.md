# CellValue

LTools.Office.Model.CellValue — модель значения ячейки Excel.

:small_blue_diamond: *Символ `?` в типе данных указывает на то, что значение может быть null.*

| Свойство      | Тип       | Описание                 |
| ------------- | --------- | ------------------------ |
| DateTimeValue | [DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=net-5.0)? | Значение Дата-время      |
| BooleanValue  | bool?     | Значение Булевое         |
| NumericValue  | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)?   | Значение Числовое        |
| TextValue     | string    | Текстовое                |
| IsBoolean     | bool      | Признак булевого         |
| IsEmpty       | bool      | Признак пустого значения |
| IsText        | bool      | Признак текста           |
| IsNumeric     | bool      | Признак числового        |
| IsError       | bool      | Признак ошибки           |
| IsDateTime    | bool      | Признак даты-времени     |


