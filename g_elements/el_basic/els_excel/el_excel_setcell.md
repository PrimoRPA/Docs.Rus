---
description: Change cells
--- 


# Изменение ячейки

Элемент изменяет формат ячеек в Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

Чтобы изменения применились, в конце работы c файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![Элемент «Изменение ячейки»](<../../../.gitbook/assets1/windows_items/ExcelWFSetCell.png>)



## Свойства

Символ `*` в названии указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

:small_blue_diamond: **Примечание**. Знак «?» в типе данных указывает на то, что значение может быть null.

1. **Диапазон\*** *[String]* — диапазон ячеек. Пример: `"A1:D12"`. 
1. **Страница** *[String]* — название страницы с указанным диапазоном. Пример: `"List1"`.
1. **Индекс страницы** *[Int32]* — номер страницы, начинается с нуля. Если указан индекс вместо названия, то в файле допускается переименовывать страницы. Пример: `"0"`. 
1. **Цвет ячеек** *[[System.Drawing.Color?](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.color?view=net-5.0)]* — цвет ячеек диапазона. Пример: `System.Drawing.Color.Black`. 
1. **Цвет бордюра** *[System.Drawing.Color?]* — цвет бордюра ячеек диапазона. Пример: `System.Drawing.Color.Black`. 
1. **Тип бордюра** *[LTools.Office.Model.CellBorderTypes]* — тип бордюра ячеек. Возможные значения:
   * Keep —
   * None —
   * Around — 
   * Full —
   * Left —
   * Right —
   * Top —
   * Bottom —
1. **Толщина бордюра** *[LTools.Office.Model.CellBorderThicknesses]* — толщина бордюра ячеек. Возможные значения:
   * *Thin* — тонкий бордюр. Значение по умолчанию.
   * *Medium* — средняя толщина.
   * *Thick* — толстый бордюр.

