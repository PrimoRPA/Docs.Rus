# Получить атрибут

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (2) (9).png>)

![](<../../../.gitbook/assets/image (319).png>)

Компонент, производящий получение данных атрибута элементе управления. Компонент корректно работает только внутри контейнера Открыть браузер либо Присоединиться к браузеру.

| Свойство           | Тип                                  | Описание                                                     |
| ------------------ | ------------------------------------ | ------------------------------------------------------------ |
| Шаблон поиска      | String                               | Шаблон поиска элемента управления                            |
| Элемент            | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                                 |
| Атрибут            | String                               | Название атрибута элемента управления                        |
| Результат          | String                               | Переменная для сохранения данных первого найденного атрибута |
| Результат (массив) | List\<string>                        | Переменная для сохранения данных всех найденных атрибутов    |
| Таймаут\*          | Int32                                | Предельное время ожидания завершения процесса (мс)           |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
List<string> att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title");
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");		
LTools.Workflow.PrimoApp.AddToLog(wf, att[0]);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title")
#Элемент
el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");	
LTools.Workflow.PrimoApp.AddToLog(wf, att[0])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
var att = app.GetAttribute("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}", "title");
//Элемент
var el = app.FindElement("{\"Tag\":\"INPUT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"textbox js-hide-label\"},{\"Key\":\"ID\",\"Value\":\"header-search-input\"}]}");
att = app.GetAttribute(el, "title");	
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, att[0]);
```
{% endtab %}
{% endtabs %}
