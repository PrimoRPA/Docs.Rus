# Перетаскивание

![](<../../../../.gitbook/assets/image (51).png>)

Компонент, производящий перетаскивание элемента управления. Может быть перетаскивание по шаблонам поиска, и тогда должны быть заданы шаблоны поиска источника и назначения, либо по координатам с заполнением координат источника и назначения.

| Свойство                   | Тип                             | Описание                                           |
| -------------------------- | ------------------------------- | -------------------------------------------------- |
| Шаблон поиска (источник)   | String                          | Шаблон поиска перемещаемого элемента               |
| Элемент (источник)         | LTools.Desktop.Model.DUIControl | Ссылка на перемещаемый элемент                     |
| Координаты (источник)      | System.Drawing.Rectangle        | Координаты перемещаемого элемента                  |
| Шаблон поиска (назначение) | String                          | Шаблон поиска элемента назначения                  |
| Элемент (назначение)       | LTools.Desktop.Model.DUIControl | Ссылка на элемент назначения                       |
| Координаты (назначение)    | System.Drawing.Rectangle        | Координаты элемента назначения                     |
| Таймаут\*                  | Int32                           | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.DragNDrop("{\"Name\":\"Всем привет!\",\"AutomationID\":\"lbl1\",\"ClassName\":\"Text\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
		"{\"Name\":\"\",\"AutomationID\":\"txtTarget\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
		null, null, System.Drawing.Rectangle.Empty, System.Drawing.Rectangle.Empty, 10000);
//Элементы
LTools.Desktop.Model.DUIControl el_from = app.FindElement("{\"Name\":\"Всем привет!\",\"AutomationID\":\"lbl1\",\"ClassName\":\"Text\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
LTools.Desktop.Model.DUIControl el_to = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"txtTarget\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.DragNDrop(null, null, el_from, el_to, System.Drawing.Rectangle.Empty, System.Drawing.Rectangle.Empty, 10000);
//Координаты
app.DragNDrop(null, null, null, null, new System.Drawing.Rectangle(100, 150, 0, 0), new System.Drawing.Rectangle(200, 250, 0, 0));
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
app.DragNDrop("{\"Name\":\"Всем привет!\",\"AutomationID\":\"lbl1\",\"ClassName\":\"Text\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
	"{\"Name\":\"\",\"AutomationID\":\"txtTarget\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
	None, None, System.Drawing.Rectangle.Empty, System.Drawing.Rectangle.Empty, 10000)
#Элементы
el_from = app.FindElement("{\"Name\":\"Всем привет!\",\"AutomationID\":\"lbl1\",\"ClassName\":\"Text\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
el_to = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"txtTarget\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
app.DragNDrop(None, None, el_from, el_to, System.Drawing.Rectangle.Empty, System.Drawing.Rectangle.Empty, 10000)
#Координаты
app.DragNDrop(None, None, None, None, System.Drawing.Rectangle(100, 150, 0, 0), System.Drawing.Rectangle(200, 250, 0, 0))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.DragNDrop("{\"Name\":\"Всем привет!\",\"AutomationID\":\"lbl1\",\"ClassName\":\"Text\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
		"{\"Name\":\"\",\"AutomationID\":\"txtTarget\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}",
		null, null, _lib.System.Drawing.Rectangle.Empty, _lib.System.Drawing.Rectangle.Empty, 10000);
//Элементы
var el_from = app.FindElement("{\"Name\":\"Всем привет!\",\"AutomationID\":\"lbl1\",\"ClassName\":\"Text\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
var el_to = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"txtTarget\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.DragNDrop(null, null, el_from, el_to, _lib.System.Drawing.Rectangle.Empty, _lib.System.Drawing.Rectangle.Empty, 10000);
//Координаты
app.DragNDrop(null, null, null, null, new _lib.System.Drawing.Rectangle(100, 150, 0, 0), new _lib.System.Drawing.Rectangle(200, 250, 0, 0));		
```
{% endtab %}
{% endtabs %}
