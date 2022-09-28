# SAPUIComboBox

LTools.SAP.Model.SAPUIComboBox

| Свойство      | Тип                                                              | Описание          |
| ------------- | ---------------------------------------------------------------- | ----------------- |
| Element       | SAPFEWSELib.ISapComboBoxTarget                                   | Ссылка на элемент |
| Id            | String                                                           | ID элемента       |
| Items         | List<[LTools.SAP.Model.SAPUIComboBoxItem](sapuicomboboxitem.md)> | Элементы списка   |
| SelectedItem  | [SAPUIComboBoxItem](sapuicomboboxitem.md)                        | Выбранный элемент |
| ScreenLeft    | int?                                                             | Отступ слева      |
| ScreenTop     | int?                                                             | Отступ сверху     |
| Width         | int?                                                             | Ширина            |
| Height        | int?                                                             | Высота            |

| Метод                                                                | Описание        |
| -------------------------------------------------------------------- | --------------- |
| SelectItem([SAPUIComboBoxItem](sapuicomboboxitem.md) item - элемент) | Выбрать элемент |
| SelectItem(int idx - индекс элемента)                                | Выбрать элемент |
| SelectItem(string key - ключ элемента)                               | Выбрать элемент |

