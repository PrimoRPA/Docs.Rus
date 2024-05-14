# Присутствие элемента

![](../../resources/basic/desktop/image-element-exist.png)

Компонент, производящий поиск элемента управления. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство        | Тип                             | Описание                                             |
| --------------- | ------------------------------- | ---------------------------------------------------- |
| Шаблон поиска\* | String                          | Шаблон поиска элемента управления                    |
| Элемент         | LTools.Desktop.Model.DUIControl | Переменная для хранения ссылки на элемент управления |
| Элементы        | List<LTools.Desktop.Model.DUIControl> | Переменная для хранения ссылки на элементы управления |
| Результат       | Boolean                         | Переменная, хранящая результаты поиска               |
| Таймаут\*       | Int32                           | Предельное время ожидания завершения процесса (мс)   |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
var el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
```
{% endtab %}
{% endtabs %}
