# Исчезновение элемента

![](<../../../../.gitbook/assets/image (158).png>)

Компонент, ожидающий исчезновение элемента управления.

| Свойство        | Тип    | Описание                                           |
| --------------- | ------ | -------------------------------------------------- |
| Шаблон поиска\* | String | Шаблон поиска элемента управления                  |
| Таймаут\*       | Int32  | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.WaitElementVanish("{\"Name\":\"Vanish Label\",\"AutomationID\":\"\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 2000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.WaitElementVanish("{\"Name\":\"Vanish Label\",\"AutomationID\":\"\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 2000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.WaitElementVanish("{\"Name\":\"Vanish Label\",\"AutomationID\":\"\",\"ClassName\":\"TextBlock\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 2000);
```
{% endtab %}
{% endtabs %}
