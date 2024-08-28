---
Description: Get list
---

# Получение списка

![](../../../.gitbook/assets1/getlist-activity.png)

Компонент, получающий значения из комбо-бокса или списка.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Вывод**
1. **Выбранные** *[List\<String>]* - Выбранные значения списка  
1. **Значения** *[List\<String>]* - Все значения списка  

**Процесс**
1. **Шаблон поиска** *[String]* - Шаблон поиска элемента управления  
1. **Элемент** *[LTools.Desktop.Model.DUIControl]* - Ссылка на элемент управления  
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс)  

## Только код  
Пример использования элемента в процессе с типом **Только код** (Pure code):
> - Для работы с примером необходимо установить приложение **mate-calc**.
> - Для демонстрации компонента `Получение списка` необходимо переключиться в режим калькулятора `Финансовый`.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Весь список
List<string> lst = app.SelectGetItems("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}");
//Элемент + Выбранные записи
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}");
List<string> sel = app.SelectGetSelItems(el);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска + Весь список
lst = app.SelectGetItems("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}")
#Элемент + Выбранные записи
el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}")
sel = app.SelectGetSelItems(el)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска + Весь список
var lst = app.SelectGetItems("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}");
//Элемент + Выбранные записи
var el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"combo box\",\"Items\":[]}]}");
var sel = app.SelectGetSelItems(el);
```
{% endtab %}
{% endtabs %}
