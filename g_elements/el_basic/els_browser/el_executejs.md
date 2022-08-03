# Выполнить JS

![](<../../../.gitbook/assets/image (708).png>)

![](<../../../.gitbook/assets/image (136).png>)

Компонент, выполняющий скрипт JS в браузере.

| Свойство  | Тип    | Описание                                           |
| --------- | ------ | -------------------------------------------------- |
| Скрипт\*  | String | Выполняемый скрипт                                 |
| Таймаут\* | Int32  | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Eval("script", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
app.Eval("script", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Eval("script", 10000);
```
{% endtab %}
{% endtabs %}
