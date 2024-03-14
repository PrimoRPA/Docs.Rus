---
description: Set cell formula
---

# Ввод формулы в ячейку

Элемент записывает формулу в ячейку Excel.

![](<../../../.gitbook/assets/Ввод формулы в ячейку. Excel.png>)

**Примечания**:

1. Путь до файла, тип драйвера и другие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, то после ввода формулы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип    | Описание                                                                                                  | Пример        |
| --------------- | ------ | --------------------------------------------------------------------------------------------------------- | ------------- |
| **Excel:**    |        |                                                                                                           |               |
| Ячейка\*        | String | Идентификатор ячейки для ввода формулы                                                                    | `"A3"`        |
| Формула\*       | String | Формула, которую нужно записать в ячейку. Оба драйвера (Interop и DX) поддерживают ввод формулы на русском и английском языках  | `"=СУММ(A1:A2)"`  |
| Страница        | String | Наименование страницы Excel, на которой находится ячейка                                                  | `"List 1"`    |
| Индекс страницы | Int32  | Порядковый номер страницы. Отсчет начинается с 0                                                          | `0`           |


## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код (Pure code)** на допустимых языках:

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//text - Формула: [String] Формула, вводимая в ячейку
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//app.WriteCellFormula(cell, text, [sheet], [sheetIdx], [numFormat]);
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
String text="=SUM(C1:C11)";
app.WriteCellFormula("C12",text,"Лист2", 1);
app.Calculate();
app.SaveAs(".\\formula.xlsx");
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#cell - Ячейка: [String] Идентификатор ячейки (A4)
#text - Формула: [String] Формула, вводимая в ячейку
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#app.WriteCellFormula(cell, text, [sheet], [sheetIdx], [numFormat])
		
app = LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx",";", LTools.Office.Model.InteropTypes.DX)
text = "=SUM(C1:C10)"
app.WriteCellFormula("C11", text, "Лист2", 1)
app.Calculate();
app.SaveAs(".\\formula.xlsx");
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//text - Формула: [String] Формула, вводимая в ячейку
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//app.WriteCellFormula(cell, text, [sheet], [sheetIdx], [numFormat]);
		
let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var text = "=SUM(C1:C10)";
app.WriteCellFormula("C11", text, "Лист2", 1);
app.Calculate();
app.SaveAs(".\\formula.xlsx");
```
{% endtab %}
{% endtabs %}
