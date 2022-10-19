# Получить активное окно

![](<../../../.gitbook/assets/Получить активное окно.png>)

Компонент, получающий активное окно рабочего стола.


| Свойство      | Тип                             | Описание                                           |
| ------------- | ------------------------------- | -------------------------------------------------- |
| Окно          | LTools.Desktop.UIAutoDUI.UIWindow | Информация об окне                               |


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.UIAutoDUI.UIWindow win = LTools.Desktop.DesktopApp.GetActiveWindow(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
win = LTools.Desktop.DesktopApp.GetActiveWindow(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var win = _lib.LTools.Desktop.DesktopApp.GetActiveWindow(wf);
```
{% endtab %}
{% endtabs %}
