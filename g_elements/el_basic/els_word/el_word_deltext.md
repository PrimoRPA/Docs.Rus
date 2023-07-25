# Удалить текст

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (94).png>)

![](<../../../.gitbook/assets/image (3) (1).png>)

Удаляет диапазон заданной длины. Если ни начало, ни длина не указаны, удаляется весь текст.

| Свойство | Тип   | Описание      |
| -------- | ----- | ------------- |
| Начало   | Int32 | Начало текста |
| Длина    | Int32 | Длина текста  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.DeleteText(10, 100);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.DeleteText(10, 100)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.DeleteText(10, 100);
```
{% endtab %}
{% endtabs %}
