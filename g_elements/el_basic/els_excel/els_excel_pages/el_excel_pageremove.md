# Удалить страницу

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (124).png>)

![](<../../../../.gitbook/assets/image (47).png>)

Компонент, удаляющий страницу Excel.

| Свойство | Тип   | Описание        |
| -------- | ----- | --------------- |
| Индекс\* | Int32 | Индекс страницы |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SheetDelete(1);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SheetDelete(1)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SheetDelete(1);
```
{% endtab %}
{% endtabs %}
