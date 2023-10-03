# Выбор значения

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (272).png>)

![](<../../../../.gitbook/assets/image (353).png>)

Компонент, выбирающий значения в комбо-боксе либо списке.

| Свойство      | Тип                                  | Описание                                           |
| ------------- | ------------------------------------ | -------------------------------------------------- |
| Шаблон поиска | String                               | Шаблон поиска элемента управления                  |
| Элемент       | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                       |
| Значение      | String                               | Выбираемое значение                                |
| Значения      | List\<String>                        | Список выбираемых значений                         |
| Индекс        | Int32                                | Индекс значения                                    |
| Индексы       | List\<Int32>                         | Индексы значений                                   |
| Очистить      | bool                                 | Очистить список перед выбором                      |
| Таймаут\*     | Int32                                | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска + Наименование
app.SelectItem("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}", new List<string>() { "Item2" });
//Элемент + Индекс + Очистка
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}");
app.SelectItem(el, new List<int>() { 3 }, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска + Наименование
app.SelectItem("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}", List[System.String](["Item2"]))
#Элемент + Индекс + Очистка
el = app.FindElement("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}")
app.SelectItem(el, List[int]([3]), True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска + Наименование
var items = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
items.Add("Item2");
app.SelectItem("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}", items);
//Элемент + Индекс + Очистка
var idx = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Int32));
idx.Add(3);
var el = app.FindElement("{\"Tag\":\"SELECT\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"ID\",\"Value\":\"lstbxList\"}]}");
app.SelectItem(el, idx, true);
```
{% endtab %}
{% endtabs %}
