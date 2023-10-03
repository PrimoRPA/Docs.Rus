# Ввод текста

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (74).png>)

![](<../../../../.gitbook/assets/image (292).png>)

Компонент, производящий ввод текста в выбранный элемент управления. Компонент корректно работает только внутри контейнера "Открыть браузер" либо "Присоединиться к браузеру".

| Свойство      | Тип                                  | Описание                                           |
| ------------- | ------------------------------------ | -------------------------------------------------- |
| Шаблон поиска | String                               | Шаблон поиска элемента управления                  |
| Элемент       | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                       |
| Текст\*       | String                               | Вводимый текст                                     |
| Таймаут\*     | Int32                                | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
app.TextInput("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "Text");
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
app.TextInput(el, "Text");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
app.TextInput("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "Text")
#Элемент
el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}")
app.TextInput(el, "Text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
app.TextInput("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "Text");
//Элемент
var el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
app.TextInput(el, "Text");	
```
{% endtab %}
{% endtabs %}
