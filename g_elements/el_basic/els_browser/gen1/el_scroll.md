# Прокрутка

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (221).png>)

![](<../../../../.gitbook/assets/image (274).png>)

Элемент, осуществляющий прокрутку в браузере.

| Свойство       | Тип                  | Описание                                           |
| -------------- | -------------------- | -------------------------------------------------- |
| Горизонтальная | int?                 | Горизонтальная прокрутка (смещение)                |
| Вертикальная   | int?                 | Вертикальная прокрутка (смещение)                  |
| Прокрутка      | System.Windows.Point | Текущее состояние прокрутки                        |
| Таймаут\*      | Int32                | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
System.Windows.Point ret = app.Scroll(null, null);
app.Scroll(100, 20, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
ret = app.Scroll(None, None)
app.Scroll(100, 20, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
var ret = app.Scroll(null, null);
app.Scroll(100, 20, 10000);
```
{% endtab %}
{% endtabs %}
