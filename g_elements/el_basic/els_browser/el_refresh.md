# Обновить

![](<../../../.gitbook/assets/image (687).png>)

![](<../../../.gitbook/assets/image (184).png>)

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
