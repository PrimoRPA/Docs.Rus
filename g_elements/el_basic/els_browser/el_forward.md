# Вперед

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (74).png>)

![](<../../../.gitbook/assets/image (267).png>)

Компонент, осуществляющий навигацию вперед.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
app.NavigateForward();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
app.NavigateForward()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
app.NavigateForward();
```
{% endtab %}
{% endtabs %}
