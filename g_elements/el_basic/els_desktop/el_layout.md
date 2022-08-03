# Раскладка

![](<../../../.gitbook/assets/image (83).png>)

Элемент, осуществляющий смену раскладки клавиатуры.

| Свойство  | Тип           | Описание                                           |
| --------- | ------------- | -------------------------------------------------- |
| Раскладка | String        | Раскладка для установки                            |
| Раскладка | String        | Текущая раскладка клавиатуры                       |
| Раскладки | List\<String> | Имеющиеся раскладки                                |
| Таймаут\* | Int32         | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SwitchLayout("ru-RU", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SwitchLayout("ru-RU", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SwitchLayout("ru-RU", 10000);
```
{% endtab %}
{% endtabs %}
