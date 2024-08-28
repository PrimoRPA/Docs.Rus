---
Description: Hotkey simulation
---

# Эмуляция спецкнопки

![](../../../.gitbook/assets1/emul-button-activity.png)

Предназначен для эмуляции нажатия клавиш клавиатуры или их комбинаций. Этот элемент часто используется для автоматизации действий, требующих ввода с клавиатуры.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. 
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Спецкнопки\*** *[String]* - Нажимаемые Спецкнопки ("Return").  
1. **Пауза\*** *[Int32]* - Пауза между нажатиями кнопок (мс).  
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс). 

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
> Для работы с примером необходимо установить приложение **mate-calc**.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"editbar\",\"Items\":[]}]}");
LTools.Desktop.DesktopApp.TypeSimulate(wf, "100+23", 500, 20000);
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "Return");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Калькулятор", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SetFocus("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"editbar\",\"Items\":[]}]}")
LTools.Desktop.DesktopApp.TypeSimulate(wf, "100+23", 500, 20000)
LTools.Desktop.DesktopApp.HotKeySimulate(wf, "Return")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":null,\"TextSearchMode\":0,\"Items\":[{\"Role\":\"editbar\",\"Items\":[]}]}");
_lib.LTools.Desktop.DesktopApp.TypeSimulate(wf, "100+23", 500, 20000);
_lib.LTools.Desktop.DesktopApp.HotKeySimulate(wf, "Return");
```
{% endtab %}
{% endtabs %}
