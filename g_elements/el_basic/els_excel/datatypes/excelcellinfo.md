# ExcelCellInfo

LTools.Office.Model.ExcelCellInfo — информация о ячейке Excel. 

:small_blue_diamond: *Символ `?` в типе данных указывает на то, что значение может быть null.*

| Свойство         | Тип                                           | Описание                                          |
| ---------------- | --------------------------------------------- | ------------------------------------------------- |
| Value            | [LTools.Office.Model.CellValue](cellvalue.md) | Значение ячейки                                   |
| TextValue        | String                                        | Текстовое значение ячейки                         |
| BackroundColor   | [System.Drawing.Color](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.color?view=net-6.0&viewFallbackFrom=netstandard-1.0) | Цвет фона
| FontColor        | System.Drawing.Color                          | Цвет шрифта                                       |
| BorderType       | LTools.Office.Model.ExcelBorderTypes?         | Тип бордюра                                       |
| CustomBorderType | LTools.Office.Model.ExcelCustomBorderTypes\[] | Бордюры при использовании ExcelBorderTypes.Custom |
| Height           | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)? | Высота строки (определяется первой ячейкой)       |



