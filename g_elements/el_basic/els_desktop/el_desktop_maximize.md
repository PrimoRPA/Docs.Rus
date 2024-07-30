# Развернуть окно

*Eng: Maximize window*

![](<../../../.gitbook/assets/image (68).png>)

Элемент позволяет развернуть окно указанного приложения на полный экран. Это полезно в сценариях автоматизации, где требуется максимальная видимость всех элементов пользовательского интерфейса. Элемент корректно работает только внутри контейнера [**Присоединиться к приложению**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_desktop/el_desktop_attach).



Описание общих свойств см. в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements).

| Свойство  | Тип   | Описание                                           |
| --------- | ----- | -------------------------------------------------- |
| Таймаут\* | Int32 | Предельное время ожидания завершения процесса (мс) |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Maximize();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.Maximize()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.Maximize();
```
{% endtab %}
{% endtabs %}
