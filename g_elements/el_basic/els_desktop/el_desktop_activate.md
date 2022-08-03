# Активировать процесс

![](<../../../.gitbook/assets/image (37).png>)

Компонент, выводящий окно процесса на передний план. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство  | Тип   | Описание                                           |
| --------- | ----- | -------------------------------------------------- |
| Таймаут\* | Int32 | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, "Calc*", null, 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Activate();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, "Calc*", None, 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Activate()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Desktop.DesktopApp.Init(wf, "Calc*", null, 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Activate();
```
{% endtab %}
{% endtabs %}
