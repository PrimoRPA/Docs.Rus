# SAPUITree

LTools.SAP.Model.SAPUITree

| Свойство     | Тип                                                      | Описание          |
| ------------ | -------------------------------------------------------- | ----------------- |
| Element      | SAPFEWSELib.ISapTreeTarget                               | Ссылка на элемент |
| Id           | String                                                   | ID элемента       |
| ColumnTitles | List\<string>                                            | Заголовки колонок |
| ColumnNames  | List\<string>                                            | Имена колонок     |
| Nodes        | List<[LTools.SAP.Model.SAPUITreeNode](sapuitreenode.md)> | Узлы дерева       |
| ScreenLeft   | int?                                                     | Отступ слева      |
| ScreenTop    | int?                                                     | Отступ сверху     |
| Width        | int?                                                     | Ширина            |
| Height       | int?                                                     | Высота            |

> Символ ? в типе данных указывает на то, что значение может быть null.

| Метод                                   | Описание                         |
| --------------------------------------- | -------------------------------- |
| SelectNode(String key - ключ узла)      | Выделить узел дерева             |
| DoubleClickNode(String key - ключ узла) | Осуществить двойной клик на узле |
| ExpandNode(String key - ключ узла)      | Раскрыть узел                    |
| CollapseNode(String key - ключ узла)    | Свернуть узел                    |

