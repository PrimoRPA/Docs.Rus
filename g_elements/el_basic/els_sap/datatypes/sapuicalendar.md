# SAPUICalendar

| Свойство        | Тип                      | Описание                |
| --------------- | ------------------------ | ----------------------- |
| Element         | SAPFEWSELib.ISapCalendar | Ссылка на элемент       |
| Id              | String                   | ID элемента             |
| SelectionStart  | DateTime?                | Начало диапазона дат    |
| SelectionEnd    | DateTime?                | Окончание диапазона дат |
| FocusedDate     | DateTime?                | Выбранная дата          |
| ScreenLeft      | int?                     | Отступ слева            |
| ScreenTop       | int?                     | Отступ сверху           |
| Width           | int?                     | Ширина                  |
| Height          | int?                     | Высота                  |

| Метод                                                        | Описание             |
| ------------------------------------------------------------ | -------------------- |
| SelectRange(DateTime from - начало, DateTime to - окончание) | Выбрать диапазон дат |
