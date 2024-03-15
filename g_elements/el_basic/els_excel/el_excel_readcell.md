---
description: Read cell
---

# Чтение из ячейки

Элемент считывает данные из ячейки Excel и сохраняет их в переменную. 

Путь до файла, тип драйвера и прочие параметры подключения настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets1/WFReadCell.png>)

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                         |
| -------------------- | --------------------- | -------------------------------- |
| **Excel:**  | |  |
| Ячейка\*             | String   | Идентификатор ячейки, которую нужно прочитать. Пример: `"A4"` |
| Страница             | String   | Название страницы с указанной ячейкой. Пример: `"Лист1"`      |
| Индекс страницы      | Int32    | Порядковый номер страницы, отсчет с нуля. Пример: `0`         |
| **Вывод:**  | |  |
| Данные\*             | Object   | Переменная для записи полученных данных из ячейки             |

**Пример заполненных свойств**:

![](<../../../.gitbook/assets/excel-read-cell2.png>)


## Пример использования
Проект, в котором считываются данные из ячейки, можно найти [здесь](https://github.com/PrimoRPA/Learning/tree/master/WorkWithExcelExample). Проект имеет название WorkWithExcelExample, в качестве типа процесса выбрана **Последовательность**. Чтобы просмотреть процессы проекта, загрузите его в Студию.


## Только код
Ниже приведен пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//data - Данные: [Object] Данные, полученные из ячейки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//object data = app.ReadCell(cell, [sheet], [sheetIdx]);

LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
object data = app.ReadCell("C5", "Лист1", 0);
		
//Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, data.ToString(), LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
#app - [LTools.Office.ExcelApp] Приложение Excel
#cell - Ячейка: [String] Идентификатор ячейки (A4)
#data - Данные: [Object] Данные, полученные из ячейки
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#data = app.ReadCell(cell, [sheet], [sheetIdx]) #Object

app = LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
data = app.ReadCell("F4", "Лист1", 0) #Object
		
#Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, str(data), LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//data - Данные: [Object] Данные, полученные из ячейки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//var data = app.ReadCell(cell, [sheet], [sheetIdx]); //Object

var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, "c://Users//Alex//Documents//Primo//LearningPureCode//book.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);	
var data = app.ReadCell("D5", "Лист1", 0); //Object
		
//Вывод в лог
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, data.toString(), _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}







