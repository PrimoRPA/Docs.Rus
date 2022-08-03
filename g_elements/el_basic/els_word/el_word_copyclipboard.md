# Копировать в буфер обмена

![](<../../../.gitbook/assets/image (70).png>)

Элемент копирует выделенный текст в буфер обмена.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.CopyToClipboard();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.CopyToClipboard()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.CopyToClipboard();
```
{% endtab %}
{% endtabs %}
