# Эмуляция ввода текста

![](<../../../.gitbook/assets/image (243).png>)

Компонент, производящая симуляцию ввода текста на клавиатуре. Компонент корректно работает только внутри контейнера Присоединиться к приложению.

| Свойство  | Тип    | Описание                                           |
| --------- | ------ | -------------------------------------------------- |
| Текст\*   | String | Вводимый текст                                     |
| Пауза\*   | Int32  | Пауза между нажатиями кнопок (мс)                  |
| Таймаут\* | Int32  | Предельное время ожидания завершения процесса (мс) |
| Асинхронный | Boolean | Установите флаг, если нужно использовать асинхронный ввод |
| Новое ядро | Boolean  | Установите флаг, если у Вас возникла проблема с эмулированием подчеркивания. Новое ядро помогает решить эту проблему |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
LTools.Desktop.DesktopApp.TypeSimulate(wf, "Text", 100, 20000);	
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
LTools.Desktop.DesktopApp.TypeSimulate(wf, "Text", 100, 20000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
app.SetFocus("{\"Name\":\"\",\"AutomationID\":\"txtbxSample\",\"ClassName\":\"TextBox\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
_lib.LTools.Desktop.DesktopApp.TypeSimulate(wf, "Text", 100, 20000);	
```
{% endtab %}
{% endtabs %}
