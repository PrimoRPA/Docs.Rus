# Выделить диапазон

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (84).png>)

![](<../../../.gitbook/assets/image (91).png>)

Выделяет диапазон заданной длины. Если ни начало, ни длина не указаны, выделяется весь текст.

| Свойство | Тип   | Описание         |
| -------- | ----- | ---------------- |
| Начало   | Int32 | Начало выделения |
| Длина    | Int32 | Длина выделения  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.SelectRange(100, 50);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.SelectRange(100, 50)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.SelectRange(100, 50);
```
{% endtab %}
{% endtabs %}
