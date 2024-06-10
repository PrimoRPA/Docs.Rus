# Чтение диапазона

![](<../../../../.gitbook/assets1/cropped-readrange-fixed.png>)

Компонент читает данные из диапазона ячеек. Компонент работает корректно только внутри контейнера "Таблица ODF".

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Диапазон** *[String]*: Диапазон считывания ячеек. Пример: `"A1:D12"`. Если указать в качестве значения `*`, будет прочитан весь лист.
2. **Страница** *[String]*: Название страницы. Пример: `"List1"`.
3. **Индекс страницы** *[Int32]*: Индекс страницы - порядковый номер листа в файле таблиц. Отсчет начинается с 0. Пример: `1`.
4. **Формат даты**: Явное указание формата даты.
5. **Строка заголовков** *[Boolean]*: Признак того, что первая строка содержит заголовки.
6. **Переменная (текст)** *[List\<List\<string>>]*: Переменная для хранения результатов чтения в виде текстовых значений.
7. **Переменная (информация)** *[List\<List \<[Primo.Office.OdfOxml.Model.ExcelCellInfo]]*: Переменная для хранения результатов чтения дополнительной информации о ячейках: например, о цвете шрифта.
8. **Переменная (таблица)** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-6.0)]*: Переменная для хранения результатов чтения в табличном виде.
9. **Учитывать типы полей ячеек Excel** *[Boolean]*: Нужно ли учитывать типы ячеек таблицы.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

{% tabs %}
{% tab title="C#" %}
```csharp
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);  
List<List<string>> dataList = app.ReadRange(range, [sheet], [sheetIdx]);  
List<List<Primo.Office.OdfOxml.Model.ExcelCellInfo>> dataCells = app.ReadRangeInfo(range, [sheet], [sheetIdx]);  
System.Data.DataTable dataTable = app.ReadRangeTable(range, [sheet], [sheetIdx]);`
```
{% endtab %}

{% tab title="Python" %}
```python
app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file])
dataList = app.ReadRange(range, [sheet], [sheetIdx])
dataCells = app.ReadRangeInfo(range, [sheet], [sheetIdx])
dataTable = app.ReadRangeTable(range, [sheet], [sheetIdx]) 
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
let data = app.ReadRange(range, [sheet], [sheetIdx]);
let data = app.ReadRangeInfo(range, [sheet], [sheetIdx]); 
let data = app.ReadRangeTable(range, [sheet], [sheetIdx]);
```
{% endtab %}
{% endtabs %}
