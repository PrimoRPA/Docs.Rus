---
description: Read cell formula
---

# Чтение формулы из ячейки

Элемент считывает формулу из указанной ячейки Excel и сохраняет ее в переменную. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets1/WFReadCellFormula.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность его заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство             | Тип                   | Описание                         | Пример  |
| -------------------- | --------------------- | -------------------------------- | ------- |
| **Excel:**  | |  |
| Ячейка\*             | String   | Ячейка, из которой нужно извлечь формулу      | `"A4"` |
| Страница             | String   | Название страницы с указанной ячейкой         | `"Лист1"` |
| Индекс страницы      | Int32    | Порядковый номер страницы в книге Excel       | `0` |
| **Вывод:**  | |  |
| Формула\*            | String   | Название переменной, в которую будет записана прочитанная формула | |



## Только код
Ниже приведен пример использования элемента в процессе с типом **Только код** (Pure code):
  
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
		
let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);	
var data = app.ReadCellFormula("G4", "Лист2", 1); //String
				
//Вывод в лог
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, data, _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}

