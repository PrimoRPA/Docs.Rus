# Разрешение

*Eng: Screen resolution*

![](<../../../.gitbook/assets/image (111).png>)

Элемент изменяет разрешение экрана. Используется в задачах, требующих установки определенного разрешения экрана.

**Процесс:**  
1. **Вертикальное** *[int?]* — вертикальное разрешение.  
1. **Горизонтальное** *[int?]* — горизонтальное разрешение.   
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса (мс).  

**Вывод:**
1. **Разрешение** *[System.Windows.Point?]* — текущее разрешение экрана.  


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

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
