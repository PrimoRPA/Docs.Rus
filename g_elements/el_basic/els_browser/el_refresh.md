# Обновить

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (115).png>)

![](<../../../.gitbook/assets/image (414).png>)

Компонент, осуществляющий обновление страницы.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
app.Refresh();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
app.Refresh()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
app.Refresh();
```
{% endtab %}
{% endtabs %}
