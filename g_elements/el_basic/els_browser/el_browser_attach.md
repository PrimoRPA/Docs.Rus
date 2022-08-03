# Присоединиться к браузеру

![](<../../../.gitbook/assets/image (134).png>)

Компонент, осуществляющий подключение к действующему браузеру.

| Свойство           | Тип                                 | Описание                                                                                        |
| ------------------ | ----------------------------------- | ----------------------------------------------------------------------------------------------- |
| Тип браузера       | LTools.WebBrowser.Model.BowserTypes | Тип используемого браузера, доступны типы: Internet Explorer (IE), Chrome, Firefox, Opera, Edge |
| Заголовок браузера | String                              | Заголовок подключаемого браузера                                                                |
| Переменная         | LTools.WebBrowser.BrowserInst       | Переменная, содержащая ссылку на подключенный браузер                                           |
| Таймаут\*          | Int32                               | Предельное время ожидания завершения процесса (мс)                                              |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
```
{% endtab %}
{% endtabs %}
