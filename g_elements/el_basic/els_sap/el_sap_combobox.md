# Комбо-бокс

![](<../../../.gitbook/assets/image (430).png>)

Элемент, получающий указатель на UI-элемент Комбо-бокс.

| Свойство         | Тип                                                                         | Описание                                           |
| ---------------- | --------------------------------------------------------------------------- | -------------------------------------------------- |
| Окно             | String                                 | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента      | String                                                                      | ID элемента                                        |
| Элемент          | LTools.SAP.Model.SAPUIItem                                                  | Ссылка на элемент управления                       |
| Комбо-бокс       | [LTools.SAP.Model.SAPUIComboBox](datatypes/sapuicombobox.md)                | Переменная, хранящая ссылку на комбо-бокс          |
| Список           | List <[LTools.SAP.Model.SAPUIComboBoxItem](datatypes/sapuicomboboxitem.md)> | Список значений комбо-бокса                        |
| Переменная       | [LTools.SAP.Model.SAPUIComboBox](datatypes/sapuicombobox.md)                | Переменная для сохранения ссылки на комбо-бокс     |
| Значение         | [LTools.SAP.Model.SAPUIComboBoxItem](datatypes/sapuicomboboxitem.md)        | Текущее значение                                   |
| Выбрать (ключ)   | String                                                                      | Выбрать значение по ключу                          |
| Выбрать (индекс) | Int32                                                                       | Выбрать значение по индексу                        |
| Таймаут\*        | Int32                                                                       | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUIComboBox cmb = app.ComboBox("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
cmb.SelectItem(cmb.Items[0].Id);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
cmb = app.ComboBox("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
cmb.SelectItem(cmb.Items[0].Id)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var cmb = app.ComboBox("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
cmb.SelectItem(cmb.Items[0].Id);
```
{% endtab %}
{% endtabs %}

