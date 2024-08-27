# Выбрать элемент

*Eng: Check element*

![](<../../../../.gitbook/assets/image (82).png>)

Компонент, производящий выбор состояния выбранного элемента управления (для чек-боксов и радио-кнопок).

| Свойство        | Тип                                   | Описание                                           |
| --------------- | ------------------------------------- | -------------------------------------------------- |
| Шаблон поиска   | String                                | Шаблон поиска элемента управления                  |
| Элемент         | LTools.WebBrowser. Model.IElementInfo | Ссылка на элемент управления                       |
| Новое состояние | Boolean                               | Устанавливаемое состояние                          |
| Состояние       | Bool?                               | Текущее состояние                                  |
| Таймаут\*       | Int32                                 | Предельное время ожидания завершения процесса (мс) |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
app.SetIsChecked("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", true);
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
app.SetIsChecked(el, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
app.SetIsChecked("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", True)
#Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}")
app.SetIsChecked(el, True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
app.SetIsChecked("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", true);
//Элемент
var el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
app.SetIsChecked(el, true);
```
{% endtab %}
{% endtabs %}
