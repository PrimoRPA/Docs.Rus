# Восстановить окно

![](<../../../.gitbook/assets/image (241).png>)

Компонент, восстанавливающий окно приложения. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство  | Тип   | Описание                                           |
| --------- | ----- | -------------------------------------------------- |
| Таймаут\* | Int32 | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "*Notepad*", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Restore();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "*Notepad*", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Restore()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "*Notepad*", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Restore();
```
{% endtab %}
{% endtabs %}
