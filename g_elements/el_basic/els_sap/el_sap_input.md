# Ввод текста

![](<../../../.gitbook/assets/image (27).png>)

Компонент, производящий ввод текста в выбранный элемент управления. Компонент корректно работает только внутри контейнера SAP.

| Свойство    | Тип                        | Описание                                           |
| ----------- | -------------------------- | -------------------------------------------------- |
| ID элемента | String                     | ID элемента                                        |
| Элемент     | LTools.SAP.Model.SAPUIItem | Ссылка на элемент управления                       |
| Текст\*     | String                     | Вводимый текст                                     |
| Таймаут\*   | Int32                      | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
app.TypeText("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", "test");
LTools.SAP.Model.SAPUIItem item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", 10000);
app.TypeText(item, "test");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf);
app.TypeText("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", "test")
item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", 10000)
app.TypeText(item, "test")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
app.TypeText("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", "test");
var item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", 10000);
app.TypeText(item, "test");
```
{% endtab %}
{% endtabs %}
