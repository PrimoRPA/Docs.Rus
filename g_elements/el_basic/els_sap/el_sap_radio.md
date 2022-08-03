# Радио-кнопка

![](<../../../.gitbook/assets/image (400).png>)

Элемент, получающий указатель на UI-элемент Радио-кнопка.

| Свойство     | Тип                                                                | Описание                                           |
| ------------ | ------------------------------------------------------------------ | -------------------------------------------------- |
| ID элемента  | String                                                             | ID элемента                                        |
| Элемент      | LTools.SAP.Model.SAPUIItem                                         | Ссылка на элемент управления                       |
| Радио-кнопка | [LTools.SAP.Model.SAPUIRadioButton](datatypes/sapuiradiobutton.md) | Переменная, хранящая ссылку на радио-кнопку        |
| Переменная   | [LTools.SAP.Model.SAPUIRadioButton](datatypes/sapuiradiobutton.md) | Переменная для сохранения ссылки на радио-кнопку   |
| Выбрана      | Boolean                                                            | Признак выбранной кнопки                           |
| Выбрать      | Boolean                                                            | Выбрать радио-кнопку                               |
| Таймаут\*    | Int32                                                              | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUIRadioButton rad = app.RadioButton("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
rad.IsSelected = true;
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
rad = app.RadioButton("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
rad.IsSelected = True
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var rad = app.RadioButton("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
rad.IsSelected = true;
```
{% endtab %}
{% endtabs %}
