# Получение списка

![](<../../../../.gitbook/assets/image (107).png>)

Компонент, получающий значения из комбо-бокса либо списка.

| Свойство      | Тип                             | Описание                                           |
| ------------- | ------------------------------- | -------------------------------------------------- |
| Шаблон поиска | String                          | Шаблон поиска элемента управления                  |
| Элемент       | LTools.Desktop.Model.DUIControl | Ссылка на элемент управления                       |
| Значения      | List\<String>                   | Все значения списка                                |
| Выбранные     | List\<String>                   | Выбранные значения списка                          |
| Таймаут\*     | Int32                           | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Весь список
List<string> lst = app.SelectGetItems("{\"Name\":\"\",\"AutomationID\":\"lstbxListBox\",\"ClassName\":\"ListBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
//Элемент + Выбранные записи
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"lstbxListBox\",\"ClassName\":\"ListBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
List<string> sel = app.SelectGetSelItems(el);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска + Весь список
lst = app.SelectGetItems("{\"Name\":\"\",\"AutomationID\":\"lstbxListBox\",\"ClassName\":\"ListBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
#Элемент + Выбранные записи
el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"lstbxListBox\",\"ClassName\":\"ListBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
sel = app.SelectGetSelItems(el)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Весь список
var lst = app.SelectGetItems("{\"Name\":\"\",\"AutomationID\":\"lstbxListBox\",\"ClassName\":\"ListBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
//Элемент + Выбранные записи
var el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"lstbxListBox\",\"ClassName\":\"ListBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
var sel = app.SelectGetSelItems(el);
```
{% endtab %}
{% endtabs %}
