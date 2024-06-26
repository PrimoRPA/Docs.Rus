# Чтение диапазона

Элемент считывает данные из диапазона ячеек ODF-таблицы. Путь до файла указывается в контейнере «Таблица ODF».

![Элемент «Чтение диапазона»](<../../../../.gitbook/assets1/windows_items/odf-read-range.png>)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

Группа свойств «Таблица»:

1. **Диапазон** *[String]* — диапазон считывания ячеек. Пример: `"A1:D12"`. Если не указывать значение, то будет прочитан выделенный диапазон. Если указать в качестве значения `*`, будет прочитан весь лист.
1. **Страница** *[String]* — наименование страницы. Пример: `"List1"`.
1. **Индекс страницы** *[Int32]* — порядковый номер страницы. Нумерация начинается с нуля. Пример: `0`.
1. **Формат даты** — явное указание формата даты. 

Группа свойств «Вывод»:

1. **Переменная (таблица)** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0)]* — переменная для хранения результатов в табличном виде.
1. **Переменная (текст)** *[List\<List\<string>>]* — переменная для хранения результатов в виде текстовых значений.
1. **Переменная (информация)** *[List\<List \<[LTools.Office.Model.ExcelCellInfo](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/datatypes/excelcellinfo)>>]* — переменная для хранения дополнительной информации, прочитанной о ячейках: например, о цвете шрифта.
1. **Строка заголовков** *[Boolean]* — признак того, что первая строка содержит заголовки.
1. **Учитывать типы полей ячеек Excel** *[Boolean]* — нужно ли учитывать типы ячеек в таблице Excel.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
```
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
List<List<string>> data = app.ReadRange(range, [sheet], [sheetIdx]);
List<List<LTools.Office.Model.ExcelCellInfo>> data = app.ReadRangeInfo(range, [sheet], [sheetIdx]);
System.Data.DataTable data = app.ReadRangeTable(range, [sheet], [sheetIdx]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
