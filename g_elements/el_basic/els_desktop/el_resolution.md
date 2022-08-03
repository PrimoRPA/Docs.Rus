# Разрешение

![](<../../../.gitbook/assets/image (111).png>)

Элемент, осуществляющий смену разрешения экрана.

| Свойство       | Тип                  | Описание                                           |
| -------------- | -------------------- | -------------------------------------------------- |
| Горизонтальное | int?                 | Горизонтальное разрешение                          |
| Вертикальное   | int?                 | Вертикальное разрешение                            |
| Разрешение     | System.WIndows.Point | Текущее разрешение экрана                          |
| Таймаут\*      | Int32                | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.ChangeResolution(1920, 1080, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.ChangeResolution(1920, 1080, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.ChangeResolution(1920, 1080, 10000);
```
{% endtab %}
{% endtabs %}
