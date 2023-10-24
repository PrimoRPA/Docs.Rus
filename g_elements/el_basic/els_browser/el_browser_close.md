# Закрыть браузер 
*Eng: CloseBrowser*

Элемент завершает работу браузера. Может быть полезен, когда необходимо завершить работу с браузером после выполнения всех необходимых действий. Например, после того как собраны нужные данные с веб-страницы, закрытие браузера поможет освободить ресурсы и завершить текущий процесс робота.

![](<../../../.gitbook/assets/image (377).png>)

Должен размещаться внутри контейнера [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) либо [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach).

## Свойства

Элемент обладает только общими свойствами, описанными [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa). Уникальные свойства отсутствуют.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Close();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
app.Close()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Close();
```
{% endtab %}
{% endtabs %}
