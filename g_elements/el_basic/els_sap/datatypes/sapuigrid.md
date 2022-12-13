# SAPUIGrid

LTools.SAP.Model.SAPUIGrid

| Свойство       | Тип                                                             | Описание                               |
| -------------- | --------------------------------------------------------------- | -------------------------------------- |
| Element        | SAPFEWSELib.ISapGridViewTarget                                  | Ссылка на элемент                      |
| Id             | String                                                          | ID элемента                            |
| Columns        | List<[LTools.SAP.Model.SAPUIGridColumn](sapuigridcolumn.md)>    | Колонки                                |
| Cells          | List\<List<[LTools.SAP.Model.SAPUIGridCell](sapuigridcell.md)>> | Ячейки                                 |
| CellsDT        | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0) | Ячейки  |
| SelectedRows   | List\<int>                                                      | Индексы выбранных строк                |
| SelectedCells  | [Dictionary](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0)\<int, string>                                        | Выбранные ячейки. Индекс, Ключ колонки |
| ScrollLimit    | [System.Drawing.Point](https://learn.microsoft.com/ru-ru/dotnet/api/System.Drawing.Point?view=netcore-1.1) | Предельное значение прокрутки |
| ScrollPosition | System.Drawing.Point                                            | Текущее состояние прокрутки            |
| ScreenLeft     | int?                                                            | Отступ слева                           |
| ScreenTop      | int?                                                            | Отступ сверху                          |
| Width          | int?                                                            | Ширина                                 |
| Height         | int?                                                            | Высота                                 |

> Символ ? в типе данных указывает на то, что значение может быть null.

| Метод                                                                                      | Описание                                              |
| ------------------------------------------------------------------------------------------ | ----------------------------------------------------- |
| SelectCells(List cells - строки формата "Индекс строки, Ключ колонки" ("1, NAME"))         | Выделить ячейки                                       |
| SelectRows(List rows - индексы строк)                                                      | Выделить строки                                       |
| SetCurrentCell(int row - индекс строки, string column - ключ колонки)                      | Выбрать текущую ячейку                                |
| FocusCell(int row - индекс строки, string column - ключ колонки)                           | Выбрать текущую ячейку                                |
| ClickCell(int row - индекс строки, string column - ключ колонки)                           | Осуществляет клик на ячейке                           |
| DoubleClickCell(int row - индекс строки, string column - ключ колонки)                     | Осуществляет двойной клик на ячейке                   |
| ClickFocusedCell()                                                                         | Клик текущей ячейки                                   |
| DoubleClickFocusedCell()                                                                   | Двойной клик текущей ячейки                           |
| PressButtonCurrentCell()                                                                   | Нажимает кнопку текущей ячейки                        |
| PressEnter()                                                                               | Нажать кнопку Enter                                   |
| PressF4()                                                                                  | Нажать кнопку F4                                      |
| ScrollHorizontal(int val - значение)                                                       | Горизонтальный скролл                                 |
| ScrollVertical(int val - значение)                                                         | Вертикальный скролл                                   |
| PressToolbarButton(string id - ID кнопки)                                                  | Осуществляет клик на кнопке панели управления таблицы |
| ModifyCell(int row - индекс строки, string column - ключ колонки, string value - значение) | Изменяет значение ячейки                              |
| InsertRows(string idx - индексы строк)                                                     | Вставляет строки '1,2,4'                              |
| DeleteRows(string id - индексы строк)                                                      | Удаляет строки '1,2,4'                                |

