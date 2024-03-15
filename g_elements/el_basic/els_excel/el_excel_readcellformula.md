# Чтение формулы из ячейки

![](<../../../.gitbook/assets/excel-read-cell-formula.png>)

Элемент считывает формулу из указанной ячейки Excel. Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                         |
| -------------------- | --------------------- | -------------------------------- |
| ***Excel***  | |  |
| Ячейка\*             | String   | Ячейка, из которой нужно извлечь формулу. Пример: `"A4"`  |
| Страница             | String   | Название страницы с указанной ячейкой |
| Индекс страницы      | Int32    | Порядковый номер страницы, отсчет с 0 |
| ***Вывод***  | |  |
| Формула\*            | String   | Переменная, в которой будет храниться формула, полученная из ячейки |

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//data - Формула: [String] Формула, полученная из ячейки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//String data = app.ReadCellFormula(cell, [sheet], [sheetIdx]);
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
String data = app.ReadCellFormula("B2", "Лист1", 0);

//Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, data, LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
#app - [LTools.Office.ExcelApp] Приложение Excel
#cell - Ячейка: [String] Идентификатор ячейки (A4)
#data - Формула: [String] Формула, полученная из ячейки
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#data = app.ReadCellFormula(cell, [sheet], [sheetIdx]) #String
		
app = LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
data = app.ReadCellFormula("B2", "Лист1", 0) #String

#Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, str(data), LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//data - Формула: [String] Формула, полученная из ячейки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//var data = app.ReadCellFormula(cell, [sheet], [sheetIdx]); //String
		
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);	
var data = app.ReadCellFormula("B2", "Лист1", 0); //String
		
//Вывод в лог
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, data, _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}

