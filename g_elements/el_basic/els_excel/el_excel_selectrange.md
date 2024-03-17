# Выделение диапазона

![](<../../../.gitbook/assets/image (346).png>)

Элемент выделяет диапазон ячеек Excel.

| Свойство        | Тип    | Описание                           |
| --------------- | ------ | ---------------------------------- |
| Диапазон\*      | String | Диапазон считывания ячеек (A1:D12) |
| Страница        | String | Наименование страницы              |
| Индекс страницы | Int32  | Индекс страницы                    |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SelectRange("A1:C12", "Лист1", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SelectRange("A1:C12", "Лист1", 0)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SelectRange("A1:C12", "Лист1", 0);
```
{% endtab %}
{% endtabs %}
