# Чек-бокс

![](<../../../.gitbook/assets/image (443).png>)

Элемент, получающий указатель на UI-элемент Чек-бокс.

| Свойство          | Тип                                                          | Описание                                            |
| ----------------- | ------------------------------------------------------------ | --------------------------------------------------- |
| Окно              | String                   | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента\*     | String                                                       | ID элемента                                         |
| Элемент           | LTools.SAP.Model.SAPUIItem                                   | Ссылка на элемент управления                        |
| Чек-бокс          | [LTools.SAP.Model.SAPUICheckBox](datatypes/sapuicheckbox.md) | Переменная, хранящая ссылку на чек-бокс             |
| Переменная        | [LTools.SAP.Model.SAPUICheckBox](datatypes/sapuicheckbox.md) | Переменная для сохранения ссылки на чек-бокс        |
| Состояние         | Boolean                                                      | Состояние чек-бокса                                 |
| Сменить состояние | Boolean                                                      | Признак необходимости изменения состояния чек-бокса |
| Таймаут\*         | Int32                                                        | Предельное время ожидания завершения процесса (мс)  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUICheckBox ch = app.CheckBox("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
ch.IsChecked = true;
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
ch = app.CheckBox("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
ch.IsChecked = True
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
var ch = app.CheckBox("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
ch.IsChecked = true;
```
{% endtab %}
{% endtabs %}

