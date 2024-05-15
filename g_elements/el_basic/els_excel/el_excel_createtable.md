# Создать таблицу

Элемент создает таблицу на заданном листе Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

Чтобы изменения применились, в конце работы c файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![](../../../.gitbook/assets/excel-create-table.png)


## Свойства
Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство        | Тип    | Описание                                                                                                                                      |
| --------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------- |
| _**Excel:**_    |        |                                                                                                                                              |
| Диапазон        | String | Диапазон таблицы. Пример: `"A1:D12"`                                                                                                          |
| Наименование    | String | Наименование будущей таблицы. Пример: `"Имя_таблицы"`                                                                                         |
| Страница        | String | Наименование страницы с будущей таблицей. Пример: `"Лист1"`                                                                                 |
| Индекс страницы | Int32  | Порядковый номер страницы. Нумерация начинается с нуля. Пример: `0`                                                                          |



## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Диапазон: [String] Диапазон таблицы (A1:D12)
//name - Наименование: [String] Наименование таблицы
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//app.CreateTable(range, name, [sheet], [sheetIdx]);
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, @"c:\file.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
app.CreateTable("*", "TableName", "Лист1", 0);
app.SaveAs(@"c:\file.xlsx");
```
{% endtab %}

{% tab title="Python" %}
```python
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Диапазон: [String] Диапазон таблицы (A1:D12)
#name - Наименование: [String] Наименование таблицы
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#app.CreateTable(range, name, [sheet], [sheetIdx])
		
app = LTools.Office.ExcelApp.Init(wf, @"c:\file.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
app.CreateTable("*", "Tab", "Лист1", 0)
app.SaveAs(@"c:\file.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, @"c:\file.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);	
app.CreateTable("*", "Tab", "Лист1", 0);
app.SaveAs(@"c:\file.xlsx");
```
{% endtab %}
{% endtabs %}
