# Перейти к странице 
*Eng: Navigate*


![Navigate 2](<../../../.gitbook/assets/image (436).png>)

Этот компонент предназначен для перехода по заданному адресу в веб-браузере. Он корректно функционирует только внутри контейнера "Открыть браузер" или "Присоединиться к браузеру".

**Свойства:**

- **URL\***: Строка. Это поле требует указания URL-адреса, по которому будет осуществляться переход.

- **Таймаут\***: Целое число. Это предельное время ожидания завершения процесса (в миллисекундах).

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Navigate("mail.ru");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
app.Navigate("mail.ru")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Navigate("mail.ru");
```
{% endtab %}
{% endtabs %}
