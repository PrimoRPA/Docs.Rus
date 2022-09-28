# Перейти к странице

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (20).png>)

![](<../../../.gitbook/assets/image (436).png>)

Компонент, производящий переход по заданному адресу. Компонент корректно работает только внутри контейнера Открыть браузер либо Присоединиться к браузеру.

| Свойство  | Тип    | Описание                                           |
| --------- | ------ | -------------------------------------------------- |
| URL\*     | String | URL адреса перехода                                |
| Таймаут\* | Int32  | Предельное время ожидания завершения процесса (мс) |

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
