# Изменение ячейки

Элемент изменяет формат ячеек в ODF-таблице. Путь до файла указывается в контейнере «Таблица ODF».

Если в файле требуется сохранить изменения, то дополнительно используйте элемент «Сохранить документ».

![Элемент «Изменение ячейки»](<../../../../.gitbook/assets1/windows_items/odf-set-cell.png>)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

:small_blue_diamond: **Примечание**. Знак «?» в типе данных указывает на то, что значение может быть null.

1. **Диапазон\*** *[String]* — диапазон ячеек. Пример: `"A1:D12"`.
1. **Страница** *[String]* — наименование страницы.
1. **Индекс страницы** *[Int32]* — индекс страницы.
1. **Цвет ячеек** *[[System.Drawing.Color?](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.color?view=net-5.0)]* — цвет ячеек диапазона. Пример: `System.Drawing.Color.Black`.
1. **Цвет бордюра** *[Sуstem.Drawing.Color?]* — цвет бордюра ячеек диапазона. Пример: `System.Drawing.Color.Black`.
1. **Тип бордюра** *[LTools.Office.Model.CellBorderTypes]* — тип границы ячеек в указанном диапазоне. Возможные значения:
   * Keep — использовать тип границы, установленный в документе.
   * None — нет границы.
   * Around — внешние границы.
   * Full — все границы.
   * Left — левая граница.
   * Right — правая граница.
   * Top — верхняя граница.
   * Bottom — нижняя граница.
1. **Толщина бордюра** *[LTools.Office.Model.CellBorderThickness]* — толщина границы ячеек. Возможные значения:
   * Thin — тонкая граница. Значение по умолчанию.
   * Medium — средняя толщина.
   * Thick — толстая граница.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
```
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.SetCells(data, range, color, bcolor, thick, type, [sheet], [sheetIdx]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
