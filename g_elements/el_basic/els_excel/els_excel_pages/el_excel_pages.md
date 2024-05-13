# Список страниц

![](<../../../../.gitbook/assets/image (127).png>)

Компонент, получающий список страниц Excel.

| Свойство   | Тип           | Описание                               |
| ---------- | ------------- | -------------------------------------- |
| Переменная | List\<string> | Переменная для хранения списка страниц |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
List<string> sheets = app.GetSheets();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
sheets = app.GetSheets()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var sheets = app.GetSheets();
```
{% endtab %}
{% endtabs %}
