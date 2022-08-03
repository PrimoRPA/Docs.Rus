# Эмуляция спецкнопки

![](<../../../.gitbook/assets/image (906).png>)

Компонент, производящий эмуляцию нажатия спецкнопки. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство              | Тип                             | Описание                                                                                                                                                                                           |
| --------------------- | ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Пауза\*               | Int32                           | Пауза перед и после нажатия кнопок (мс)                                                                                                                                                            |
| Спецкнопки\*          | String                          | Нажимаемые спецкнопки ({ENTER}) '[https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send](https://docs.microsoft.com/en-us/dotnet/api/system.windows.forms.sendkeys.send)' |
| Новое ядро            | Boolean                         | Признак использования нового ядра                                                                                                                                                                  |
| Основная кнопка       | LTools.Common.Model. VirtualKey | Основная кнопка                                                                                                                                                                                    |
| Модификатор           | LTools.Common.Model. VirtualKey | Кнопка-модификатор (Ctrl, Shift...)                                                                                                                                                                |
| Дополнительная кнопка | LTools.Common.Model. VirtualKey | Дополнительная кнопка                                                                                                                                                                              |
| Таймаут\*             | Int32                           | Предельное время ожидания завершения процесса (мс)                                                                                                                                                 |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
_lib.LTools.Desktop.DesktopApp.HotKeySimulate(wf, "{ENTER}");
```
{% endtab %}
{% endtabs %}
