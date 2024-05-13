# Добавить страницу

![](<../../../../.gitbook/assets/image (242).png>)

Компонент, создающий новую страницу в Excel.

| Свойство | Тип    | Описание        |
| -------- | ------ | --------------- |
| Имя\*    | String | Имя страницы    |
| Индекс   | Int32  | Индекс страницы |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SheetAdd("new page", 3);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SheetAdd("new page", 3)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SheetAdd("new page", 3);
```
{% endtab %}
{% endtabs %}
