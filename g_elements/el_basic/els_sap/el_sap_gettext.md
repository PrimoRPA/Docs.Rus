# Получить текст

![](<../../../.gitbook/assets/image (304).png>)

Компонент, получающий текст выбранного элемента управления. Компонент корректно работает только внутри контейнера SAP.

| Свойство     | Тип                        | Описание                                           |
| ------------ | -------------------------- | -------------------------------------------------- |
| ID элемента  | String                     | ID элемента                                        |
| Элемент      | LTools.SAP.Model.SAPUIItem | Ссылка на элемент управления                       |
| Переменная\* | String                     | Переменная для хранения полученного текста         |
| Таймаут\*    | Int32                      | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
string txt = app.GetText("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
txt = app.GetText("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
var txt = app.GetText("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}
{% endtabs %}
