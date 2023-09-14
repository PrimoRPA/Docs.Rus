# Ввод текста

![](<../../../../.gitbook/assets/image (218).png>)

Компонент, производящий ввод текста в выбранный элемент управления. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство      | Тип                             | Описание                                           |
| ------------- | ------------------------------- | -------------------------------------------------- |
| Шаблон поиска | String                          | Шаблон поиска элемента управления                  |
| Элемент       | LTools.Desktop.Model.DUIControl | Ссылка на элемент управления                       |
| Текст\*       | String                          | Вводимый текст                                     |
| Таймаут\*     | Int32                           | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.TextInput("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", "11");
//Ссылка на элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.TextInput(el, "11");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Calc*", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
app.TextInput("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", "11")
#Ссылка на элемент
el = app.FindElement("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
app.TextInput(el, "11")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.TextInput("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", "11");
//Ссылка на элемент
let el = app.FindElement("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.TextInput(el, "11");
```
{% endtab %}
{% endtabs %}
