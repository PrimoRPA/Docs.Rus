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
> - Для работы с примером необходимо установить приложение **mate-calc**.
> - Для демонстрации компонента `Выбор значения` калькулятор необходимо переключить в режим `Финансовый`.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Значение
app.SelectItem("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}", new List<string>() { "Алжирский динар" });
//Элемент + Индекс + Очистка
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}");
app.SelectItem(el, new List<int>() { 1 }, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Калькулятор", 10000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска + Значение		
app.SelectItem("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}", List[String](["Алжирский динар"]))
#Элемент + Индекс + Очистка
el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}")
app.SelectItem(el, List[int]([1]), True)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 10000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Значение
var items = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
items.Add("Алжирский динар");
app.SelectItem("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}", items);
//Элемент + Индекс + Очистка
var idx = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Int32));
idx.Add(1);
var el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}");
app.SelectItem(el, idx, true);
```
{% endtab %}
{% endtabs %}

