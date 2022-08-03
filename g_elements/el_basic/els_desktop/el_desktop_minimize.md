# Свернуть окно

![](<../../../.gitbook/assets/image (214).png>)

Компонент, сворачивающий окно приложения. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство  | Тип   | Описание                                           |
| --------- | ----- | -------------------------------------------------- |
| Таймаут\* | Int32 | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Minimize();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Minimize()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Minimize();
```
{% endtab %}
{% endtabs %}
