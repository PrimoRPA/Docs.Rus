---
Description: Layout
---

# Раскладка

![](../../../.gitbook/assets1/studio-linux-elements-basic/Desktop-Layout.PNG)

Элемент, осуществляющий смену раскладки клавиатуры.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. 
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Раскладка** *[String]* - Раскладка для установки.
1. **Раскладка** *[String]* - Текущая раскладка клавиатуры.
1. **Раскладки** *[List\<String>]* - Имеющиеся раскладки.
1. **Горячая клавиша** - Сочетание клавиш для смены языка.
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

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


