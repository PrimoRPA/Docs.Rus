# Чтение диапазона

![](<../../../../.gitbook/assets/image (458).png>)

Элемент считывает данные из диапазона ячеек таблицы. Путь к файлу таблицы указывается в контейнере [МойОфис Таблица](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice/els_table/el_table_app).


## Перед началом работы

Установите в Студии библиотеку [Primo.Office.MyOffice](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/els_myoffice), поскольку данный элемент входит в состав библиотеки. 

## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Таблица**

1. **Диапазон** *[String]* — диапазон считывания ячеек (`"A1:D12"`). Если не указан, будет прочитан выделенный диапазон. Если указан символ `"*"`, будет прочитан весь лист.
1. **Страница** *[String]* — название страницы.
1. **Индекс страницы** *[Int32]* — порядковый номер страницы.

**Вывод**
1. **Переменная (текст)** *[List\<List\<String>>]* — название переменной, в которую будут сохранены результаты чтения текстовых значений.
1. **Переменная (информация)** *[List\<List<[LTools.Office. Model.ExcelCellInfo](../../els\_excel/datatypes/excelcellinfo.md)>>]* — название переменной, в которую будут сохранены результаты чтения информации о ячейках.
1. **Переменная (таблица)** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-6.0)]* — название переменной, в которую будут сохранены результаты чтения табличных значений.
1. **Строка заголовков** *[Boolean]* — признак того, что первая строка содержит заголовки (для таблицы). Если галочка установлена, то заголовки будут учитываться.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
List<List<string>> data = app.ReadRange("A4:C12", [sheet], [sheetIdx]);
List<List<LTools.Office.Model.ExcelCellInfo>> data = app.ReadRangeInfo("A4:C12", [sheet], [sheetIdx]);
System.Data.DataTable data = app.ReadRangeTable("A4:C12", [sheet], [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
data = app.ReadRange("A4:C12", [sheet], [sheetIdx]) #List<List<string>>
data = app.ReadRangeInfo("A4:C12", [sheet], [sheetIdx]) #List<List<LTools.Office.Model.ExcelCellInfo>>
data = app.ReadRangeTable("A4:C12", [sheet], [sheetIdx]) #System.Data.DataTable
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let data = app.ReadRange("A4:C12", [sheet], [sheetIdx]); //List<List<string>>
let data = app.ReadRangeInfo("A4:C12", [sheet], [sheetIdx]); //List<List<LTools.Office.Model.ExcelCellInfo>>
let data = app.ReadRangeTable("A4:C12", [sheet], [sheetIdx]); //System.Data.DataTable
```
{% endtab %}
{% endtabs %}
