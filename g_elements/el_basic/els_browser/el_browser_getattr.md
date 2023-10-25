# Получить атрибут 
_Eng: Get Attribute_

![Get Attribute 2](<../../../.gitbook/assets/image (319).png>)

Данный компонент предназначен для получения данных атрибута элемента управления. Он корректно функционирует только внутри контейнера "Открыть браузер" или "Присоединиться к браузеру".

**Свойства:**
- **Шаблон поиска**: string. Это шаблон поиска элемента управления.
- **Элемент**: LTools.WebBrowser.Model.IElementInfo. Ссылка на элемент управления.
- **Атрибут**: string. Это название атрибута элемента управления.
- **Результат**: string. Переменная для сохранения данных первого найденного атрибута.
- **Результат (массив)**: List\<string>. Переменная для сохранения данных всех найденных атрибутов.
- **Таймаут\***: int. Предельное время ожидания завершения процесса (в миллисекундах).

Примеры кода для разных языков:

### C#

```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
List<string> att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title");
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");		
LTools.Workflow.PrimoApp.AddToLog(wf, att[0]);
```

### Python

```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title")
#Элемент
el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");	
LTools.Workflow.PrimoApp.AddToLog(wf, att[0])
```

### JavaScript

```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
var att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title");
//Элемент
var el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");	
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, att[0]);
```
