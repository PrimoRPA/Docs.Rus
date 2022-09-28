# SAPUITabStrip

LTools.SAP.Model.SAPUITabStrip

| Свойство   | Тип                                            | Описание          |
| ---------- | ---------------------------------------------- | ----------------- |
| Element    | SAPFEWSELib.ISapTabbedPane                     | Ссылка на элемент |
| Id         | String                                         | ID элемента       |
| Tabs       | List<[LTools.SAP.Model.SAPUITab](sapuitab.md)> | Закладки          |
| ScreenLeft | int?                                           | Отступ слева      |
| ScreenTop  | int?                                           | Отступ сверху     |
| Width      | int?                                           | Ширина            |
| Height     | int?                                           | Высота            |

| Метод                                             | Описание          |
| ------------------------------------------------- | ----------------- |
| SelectTab([SAPUITab ](sapuitab.md)tab - закладка) | Выбирает закладку |
| SelectTab(int idx - индекс закладки)              | Выбирает закладку |
| SelectTab(string key - ключ закладки)             | Выбирает закладку |

