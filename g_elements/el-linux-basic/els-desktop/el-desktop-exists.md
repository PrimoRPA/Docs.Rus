# Присутствие элемента

![](../../../.gitbook/assets1/image-element-exist.png)

Компонент, производящий поиск элемента управления. Компонент корректно работает только внутри контейнера "Присоединиться к приложению".

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Шаблон поиска\*** *[String]* - Шаблон поиска элемента управления.  
1. **Элемент** *[LTools.Desktop.Model.DUIControl]* - Переменная для хранения ссылки на элемент управления.  
1. **Элементы** *[List<LTools.Desktop.Model.DUIControl>]* - Переменная для хранения ссылки на элементы управления.  
1. **Результат** *[Boolean]* - Переменная, хранящая результаты поиска.  
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).  

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
