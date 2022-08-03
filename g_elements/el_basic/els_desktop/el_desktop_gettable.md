# Чтение таблицы

![](<../../../.gitbook/assets/image (93).png>)

Компонент, производящий чтение данных табличного элемента управления. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство             | Тип                                                          | Описание                                           |
| -------------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Шаблон поиска        | String                                                       | Шаблон поиска элемента управления                  |
| Элемент              | LTools.Desktop.Model.DUIControl                              | Ссылка на элемент управления                       |
| Переменная           | [LTools.Desktop.Model.UIDataTable](datatypes/uidatatable.md) | Переменная для хранения результатов чтения таблицы |
| Переменная (таблица) | System.Data.DataTable                                        | Переменная для хранения результатов чтения таблицы |
| Таймаут\*            | Int32                                                        | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
LTools.Desktop.Model.UIDataTable tbl = app.ReadDataGrid("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
//Элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
tbl = app.ReadDataGrid(el);
foreach (var r in tbl.Data)
	foreach (var c in r)
		LTools.Workflow.PrimoApp.AddToLog(wf, c);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
tbl = app.ReadDataGrid("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
#Элемент
el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
tbl = app.ReadDataGrid(el)
for r in tbl.Data:
	for c in r:
		LTools.Workflow.PrimoApp.AddToLog(wf, c)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
var tbl = app.ReadDataGrid("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
//Элемент
var el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
tbl = app.ReadDataGrid(el);
for (var i = 0; i < tbl.Data.Count; i++)
	for (var j = 0; j < tbl.Data[i].Count; j++)
		_lib.LTools.Workflow.PrimoApp.AddToLog(wf, tbl.Data[i][j]);
```
{% endtab %}
{% endtabs %}

