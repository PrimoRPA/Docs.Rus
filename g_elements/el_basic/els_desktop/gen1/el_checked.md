# Выбрать элемент

![](<../../../../.gitbook/assets/image (115).png>)

Компонент, производящий изменение состояния выбранного элемента управления (для чек-боксов и радио-кнопок).

| Свойство        | Тип                             | Описание                                           |
| --------------- | ------------------------------- | -------------------------------------------------- |
| Шаблон поиска   | String                          | Шаблон поиска элемента управления                  |
| Элемент         | Tools.Desktop. Model.DUIControl | Ссылка на элемент управления                       |
| Новое состояние | Boolean?                        | Новое состояние элемента                           |
| Состояние       | Boolean?                        | Текущее состояние элемента                         |
| Таймаут\*       | Int32                           | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.SetChecked("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", true);
//Ссылка на элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.SetChecked(el, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
app.SetChecked("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", True)
#Ссылка на элемент
el = app.FindElement("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
app.SetChecked(el, True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
app.SetChecked("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", true);
//Ссылка на элемент
var el = app.FindElement("{\"AutomationID\":\"CalculatorResults\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.SetChecked(el, true);
```
{% endtab %}
{% endtabs %}
