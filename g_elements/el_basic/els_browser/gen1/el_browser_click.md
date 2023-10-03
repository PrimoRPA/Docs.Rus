# Клик мышью

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (40).png>)

![](<../../../../.gitbook/assets/image (410).png>)

Компонент, производящий клик мышью на выбранном элементе управления. Компонент корректно работает только внутри контейнера "Открыть браузер" либо "Присоединиться к браузеру".

| Свойство      | Тип                                  | Описание                                           |
| ------------- | ------------------------------------ | -------------------------------------------------- |
| Шаблон поиска | String                               | Шаблон поиска элемента управления                  |
| Элемент       | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                       |
| Кнопка мыши\* | LTools.Desktop.Model.MouseButtons    | Кнопка мыши                                        |
| Таймаут\*     | Int32                                | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
app.Click("{\"Tag\":\"BUTTON\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"btn btn-3d-green button-search\"}]}", 10000, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"BUTTON\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"btn btn-3d-green button-search\"}]}");
app.Click(el);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
app.Click("{\"Tag\":\"BUTTON\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"btn btn-3d-green button-search\"}]}", 10000, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT)
#Элемент
el = app.FindElement("{\"Tag\":\"BUTTON\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"btn btn-3d-green button-search\"}]}")
app.Click(el)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
app.Click("{\"Tag\":\"BUTTON\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"btn btn-3d-green button-search\"}]}", 10000, _lib.LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
//Элемент
var el = app.FindElement("{\"Tag\":\"BUTTON\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"btn btn-3d-green button-search\"}]}");
app.Click(el);
```
{% endtab %}
{% endtabs %}
