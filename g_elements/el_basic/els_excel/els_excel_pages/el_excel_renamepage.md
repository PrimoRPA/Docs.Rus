# Переименовать страницу

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (47).png>)

![](<../../../../.gitbook/assets/image (41).png>)

Компонент, переименовывающий страницу Excel.

| Свойство | Тип    | Описание        |
| -------- | ------ | --------------- |
| Имя\*    | String | Имя страницы    |
| Индекс\* | Int32  | Индекс страницы |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SheetRename("new name", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SheetRename("new name", 0)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SheetRename("new name", 0);
```
{% endtab %}
{% endtabs %}
