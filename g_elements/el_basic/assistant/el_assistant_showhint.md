# Подсказка

![](<../../../.gitbook/assets/image (280).png>)

Элемент, отображающий окно подсказки.

| Свойство               | Тип                                             | Описание                        |
| ---------------------- | ----------------------------------------------- | ------------------------------- |
| Текст                  | String                                          | Текст подсказки                 |
| Шрифт                  | String                                          | Имя шрифта                      |
| Размер шрифта          | Int32                                           | Размер шрифта                   |
| Цвет шрифта            | System.Windows.Media.Color                      | Цвет шрифта                     |
| Цвет бордюра           | System.Windows.Media.Color                      | Цвет бордюра                    |
| Полужирный             | bool                                            | Полужирный шрифт                |
| Наклонный              | bool                                            | Наклонный шрифт                 |
| Цвет элемента          | System.Windows.Media.Color                      | Цвет бордюра элемента           |
| Проговаривать          | Boolean                                         | Проговаривать текст             |
| Голос                  | String                                          | Голос диктора                   |
| Громкость              | Int32                                           | Громкость голоса                |
| Скорость               | Int32                                           | Скорость прочитки текста        |
| Элемент (Рабочий стол) | <p></p><p>LTools.Desktop.Model.DUIControl</p>   | Элемент рабочего стола          |
| Элемент (Браузер)      | LTools.WebBrowser.Model.IElementInfo            | Элемент браузера                |
| X                      | Int32                                           | Координата X                    |
| Y                      | Int32                                           | Координата Y                    |
| Ширина                 | Int32                                           | Ширина подсказки                |
| Высота                 | Int32                                           | Высота подсказки                |
| Затемнение             | bool                                            | Затемнение экрана               |
| Расположение           | LTools.Office.Model.Assistant.PreferedLocations | Желаемое расположение подсказки |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app_d = LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000);
var el = app_d.FindElement("{\"Name\":\"Nine\",\"AutomationID\":\"num9Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 10000);

LTools.Office.AssistantApp app = new LTools.Office.AssistantApp();
app.Text = "text";
//Приложение
app.ShowHint(el, 100, 50);
//Координаты
app.ShowHint(wf, 100, 150, 100, 50);
```
{% endtab %}

{% tab title="Python" %}
```python
app_d = LTools.Desktop.DesktopApp.Init(wf, None, "Calc*", 10000)
el = app_d.FindElement("{\"Name\":\"Nine\",\"AutomationID\":\"num9Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 10000)

app = LTools.Office.AssistantApp()
app.Text = "text"
#Приложение
app.ShowHint(el, 100, 50)
#Координаты
app.ShowHint(wf, 100, 150, 100, 50)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app_d = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Calc*", 10000);
var el = app_d.FindElement("{\"Name\":\"Nine\",\"AutomationID\":\"num9Button\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}", 10000);
var app = host.newObj(_lib.LTools.Office.AssistantApp);
app.Text = "text";
//Приложение
app.ShowHint(el, 100, 50);
//Координаты
app.ShowHint(wf, 100, 150, 100, 50);
```
{% endtab %}
{% endtabs %}

