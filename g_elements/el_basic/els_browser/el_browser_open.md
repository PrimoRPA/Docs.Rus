# Открыть браузер

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (33).png>)

![](<../../../.gitbook/assets/image (293).png>)

Компонент открывает новую вкладку в браузере.

**Исключение:** в Internet Explorer будет открываться новый экземпляр браузера.

| Свойство     | Тип                                 | Описание                                                 |
| ------------ | ----------------------------------- | -------------------------------------------------------- |
| Тип браузера | LTools.WebBrowser.Model.BowserTypes | Тип используемого браузера                               |
| Переменная   | LTools.WebBrowser.BrowserInst       | Переменная для сохранения ссылки на подключенный браузер |

**Тип браузера** - это меню выбора браузеров, в котором будет происходить открытие url и дальнейшая логика процесса.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
```
{% endtab %}
{% endtabs %}
