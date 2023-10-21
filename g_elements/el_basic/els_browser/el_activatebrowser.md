# Активировать браузер

*Eng: Activate browser*

![](<../../../.gitbook/assets/image (98).png>)
 
Выводит окно браузера на передний план экрана. Применяется, когда сценарий автоматизации требует работы с веб-интерфейсом: заполнения форм, навигации по сайту, извлечения данных или выполнения других задач.

## Свойства
Элемент обладает только общими свойствами, описанными [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa). Уникальные свойства отсутствуют.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
