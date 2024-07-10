---
Description: Element exists
---

# Присутствие элемента

![](../../../.gitbook/assets1/Desktop-ElementExists.PNG)

Компонент, производящий поиск элемента управления. Компонент корректно работает только внутри контейнера "Присоединиться к приложению".

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Шаблон поиска\*** *[String]* - Шаблон поиска элемента управления.  
1. **Элемент** *[LTools.Desktop.Model.DUIControl]* - Переменная для хранения ссылки на элемент управления.  
1. **Элементы** *[List<LTools.Desktop.Model.DUIControl>]* - Переменная для хранения ссылки на элементы управления.  
1. **Результат** *[Boolean]* - Переменная, хранящая результаты поиска.  
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).  

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
> - Для работы с примером необходимо установить приложение **mate-calc**.
> - Для демонстрации `Присутствия элемента` необходимо переключиться из режима калькулятора `Простой` в режим `Расширенный` во время запуска примера (кнопка `cos` должна появиться).

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"cosine\",\"Role\":\"push button\",\"Items\":[]}]}");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Калькулятор", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"cosine\",\"Role\":\"push button\",\"Items\":[]}]}");
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Калькулятор", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
var el = app.FindElement("{\"WinName\":null,\"WinPath\":null,\"WinId\":null,\"AppName\":\"mate-calc\",\"TextSearchMode\":0,\"Items\":[{\"Name\":\"cosine\",\"Role\":\"push button\",\"Items\":[]}]}");
```
{% endtab %}
{% endtabs %}
