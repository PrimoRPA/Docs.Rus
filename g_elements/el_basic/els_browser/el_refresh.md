# Обновить браузер
*Eng: Refresh*

Позволяет обновить страницу в веб-браузере. В процессе роботизации данный элемент может понадобиться, если необходимо регулярно мониторить изменения на каком-либо веб-ресурсе.

![](<../../../.gitbook/assets/image (414).png>)

## Свойства
Элемент обладает только общими свойствами, описанными [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa). Уникальные свойства отсутствуют.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
