# Назад

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (40).png>)

![](<../../../.gitbook/assets/image (351).png>)

Компонент, осуществляющий навигацию назад.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
app.NavigateBack();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
app.NavigateBack()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
app.NavigateBack();
```
{% endtab %}
{% endtabs %}
