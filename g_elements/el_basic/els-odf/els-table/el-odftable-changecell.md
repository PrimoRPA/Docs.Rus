# Изменение ячейки

![]   (<../../../../.gitbook/assets1/Cropped-WriteFormula.png>)

Компонент, изменяющий формат ячеек в Excel.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Диапазон** *[String]*: Диапазон ячеек. Пример: `A1:D12`.
2. **Страница** *[String]*: Наименование страницы.
3. **Индекс страницы** *[Int32]*: Индекс страницы.
4. **Цвет ячеек** *[Sуstem.Drawing.Color?]*: Цвет ячеек диапазона. Пример: `System.Drawing.Color.Black`.
5. **Цвет бордюра** *[Sуstem.Drawing.Color?]*: Цвет бордюра ячеек диапазона. Пример: `System.Drawing.Color.Black`.
6. **Тип бордюра** *[LTools.Office.Model.CellBorderTypes]*: Тип бордюра ячеек.
7. **Толщина бордюра** *[LTools.Office.Model.CellBorderThickness]*: Толщина бордюра ячеек.
