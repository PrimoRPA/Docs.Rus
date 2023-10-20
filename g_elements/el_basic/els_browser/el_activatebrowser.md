# Активировать браузер

 Activate browser
 
![](<../../../.gitbook/assets/image (98).png>)

Компонент используется в процессе, при котором веб-браузер становится активным и его окно появляется на переднем плане экрана компьютера. Это позволяет взаимодействовать с веб-страницами, запускать веб-приложения и выполнять другие действия в браузере. Применяется когда программа или сценарий автоматизации требует работы с веб-интерфейсом, таким как заполнение форм, навигация по сайту, извлечение данных или выполнение других задач.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Activate();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
app.Activate()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Activate();
```
{% endtab %}
{% endtabs %}
