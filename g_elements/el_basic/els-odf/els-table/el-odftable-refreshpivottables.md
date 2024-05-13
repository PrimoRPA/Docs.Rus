---
description: Refresh pivot tables
---
# Обновление сводных таблиц

![](../../../resources/basic/myoffice/table/odftable-refresh-pivot-tables.png)

Элемент производит обновление сводных таблиц.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code): 

{% tabs %}  
{% tab title="C#" %}  
```csharp  
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);  
app.RefreshPivotTables();  
```
{% endtab %}  
{% tab title="Python" %}  
```python  
app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file])  
app.RefreshPivotTables()  
```
{% endtab %}  
{% tab title="JavaScript" %}  
```javascript  
var app =  _lib.Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);  
app.RefreshPivotTables();  
```
{% endtab %}  
{% endtabs %}  
