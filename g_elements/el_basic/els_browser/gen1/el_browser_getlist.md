# Получение списка

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (265).png>)

![](<../../../../.gitbook/assets/image (394).png>)

Компонент, получающий значения из комбо-бокса либо списка.

| Свойство      | Тип                                  | Описание                                           |
| ------------- | ------------------------------------ | -------------------------------------------------- |
| Шаблон поиска | String                               | Шаблон поиска элемента управления                  |
| Элемент       | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                       |
| Значения      | List\<String>                        | Все значения списка                                |
| Выбранные     | List\<String>                        | Выбранные значения списка                          |
| Таймаут\*     | Int32                                | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска + Все значения
List<string> items = app.SelectGetItems("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}");
//Элемент + Выбранные значения
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}");
items = app.SelectGetSelItems(el);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска + Все значения
items = app.SelectGetItems("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}")
#Элемент + Выбранные значения
el = app.FindElement("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}")
items = app.SelectGetSelItems(el)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска + Все значения
var items = app.SelectGetItems("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}");
//Элемент + Выбранные значения
var el = app.FindElement("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}");
items = app.SelectGetSelItems(el);
```
{% endtab %}
{% endtabs %}
