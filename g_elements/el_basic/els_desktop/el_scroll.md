# Прокрутка

![](<../../../.gitbook/assets/image (224).png>)

Элемент, осуществляющий прокрутку в визуальном компоненте.

| Свойства       | Тип                             | Описание                                           |
| -------------- | ------------------------------- | -------------------------------------------------- |
| Шаблон поиска  | String                          | Шаблон поиска элемента управления                  |
| Элемент        | LTools.Desktop.Model.DUIControl | Ссылка на элемент управления                       |
| Горизонтальная | double?                         | Горизонтальная прокрутка (%)                       |
| Вертикальная   | double?                         | Вертикальная прокрутка (%)                         |
| Прокрутка      | System.Windows.Point            | Текущее состояние прокрутки                        |
| Таймаут\*      | Int32                           | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.Scroll("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 100, 50, 10000);
//Элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.Scroll(el, 100, 50, 10000);
System.Windows.Point pt = app.Scroll(el, null, null, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
app.Scroll("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 100, 50, 10000)
#Элемент
el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
app.Scroll(el, 100, 50, 10000)
pt = app.Scroll(el, None, None, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.Scroll("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 100, 50, 10000);
//Элемент
var el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.Scroll(el, 100, 50, 10000);
var pt = app.Scroll(el, null, null, 10000);
```
{% endtab %}
{% endtabs %}

