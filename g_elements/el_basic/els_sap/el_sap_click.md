# Клик мышью

![](<../../../.gitbook/assets/image (51).png>)

Компонент, производящий клик мышью на выбранном элементе управления. Компонент корректно работает только внутри контейнера SAP.

| Свойство    | Тип                     | Описание                                           |
| ----------- | ----------------------- | -------------------------------------------------- |
| ID элемента | String                  | ID элемента                                        |
| Элемент     | LTools.SAP.Model.UIItem | Ссылка на элемент управления                       |
| Таймаут\*   | Int32                   | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
app.Click("/app/con[0]/ses[0]/wnd[0]/tbar[0]/btn[0]");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
app.Click("/app/con[0]/ses[0]/wnd[0]/tbar[0]/btn[0]")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
app.Click("/app/con[0]/ses[0]/wnd[0]/tbar[0]/btn[0]");
```
{% endtab %}
{% endtabs %}
