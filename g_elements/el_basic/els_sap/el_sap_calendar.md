# Календарь

![](<../../../.gitbook/assets/image (287).png>)

Элемент, получающий указатель на UI-элемент Календарь.

| Свойство          | Тип                                                          | Описание                                           |
| ----------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| Окно              | String                  | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента\*     | String                                                       | ID элемента                                        |
| Элемент           | LTools.SAP.Model.SAPUIItem                                   | Ссылка на элемент управления                       |
| Календарь         | [LTools.SAP.Model.SAPUICalendar](datatypes/sapuicalendar.md) | Переменная, хранящая ссылку на календарь           |
| Переменная        | [LTools.SAP.Model.SAPUICalendar](datatypes/sapuicalendar.md) | Переменная для сохранения ссылки на календарь      |
| Дата              | DateTime?                                                    | Выбранная дата                                     |
| Диапазон - начало | DateTime?                                                    | Диапазон дат - начало                              |
| Диапазон - конец  | DateTime?                                                    | Диапазон дат - конец                               |
| Дата              | DateTime?                                                    | Выбрать дату                                       |
| Диапазон - начало | DateTime?                                                    | Диапазон дат - начало                              |
| Диапазон - конец  | DateTime?                                                    | Диапазон дат - конец                               |
| Таймаут\*         | Int32                                                        | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUICalendar cal = app.Calendar("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
cal.SelectRange(new DateTime(2020, 2, 24), DateTime.Now);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
cal = app.Calendar("/app/con[0]/ses[0]/wnd[0]/usr/cntlCALE_CONTROL/shellcont/shell/shellcont[0]/shell")
cal.SelectRange(DateTime(2020, 2, 24), DateTime.Now)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var cal = app.Calendar("/app/con[0]/ses[0]/wnd[0]/usr/cntlCALE_CONTROL/shellcont/shell/shellcont[0]/shell");
cal.SelectRange(new _lib.System.DateTime(2020, 2, 24), _lib.System.DateTime.Now);
```
{% endtab %}
{% endtabs %}

