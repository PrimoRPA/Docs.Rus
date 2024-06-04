# Выбор значения

![](../../../resources/activities/basic/desktop/selected-element.png)

Компонент, выбирающий значения в комбо-боксе или списке.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Шаблон поиска** *[String]* - Шаблон поиска элемента управления         
1. **Элемент** *[LTools.Desktop.Model.DUIControl* - Ссылка на элемент управления      
1. **Значение** *[String]* - Выбираемое значение  
1. **Значения** *[List\<String>]* - Список выбираемых значений  
1. **Индекс** *[Int32]* - Индекс значения  
1. **Индексы** *[List\<Int32>]* - Индексы значений  
1. **Очистить** *[Boolean]* - Очистить список перед выбором  
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс)

## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Значение
app.SelectItem("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", new List<string>() { "Item1" });
//Элемент + Индекс + Очистка
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.SelectItem(el, new List<int>() { 2 }, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска + Значение		
app.SelectItem("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", List[String](["Item1"]))
#Элемент + Индекс + Очистка
el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
app.SelectItem(el, List[int]([2]), True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Значение
var items = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
items.Add("Item1");
app.SelectItem("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", items);
//Элемент + Индекс + Очистка
var idx = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Int32));
idx.Add(2);
var el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"cmbbxCombo\",\"ClassName\":\"ComboBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
app.SelectItem(el, idx, true);
```
{% endtab %}
{% endtabs %}
