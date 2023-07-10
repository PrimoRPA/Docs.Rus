# Комбо-бокс

![](<../../../.gitbook/assets/image (430).png>)

Получает указатель на UI-элемент «комбо-бокс».

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство         | Тип                                                                         | Описание                                           |
| ---------------- | --------------------------------------------------------------------------- | -------------------------------------------------- |
| ***Процесс:***  | | |
| Окно             | String                                                                      |Заголовок окна программы, с которым планируется работать. Для его автоматического заполнения можно использовать инструмент ![](<../../../.gitbook/assets/image (794).png>) - просто наведите им на нужный заголовок |
| ID элемента      | String                                                                      | ID элемента управления                             |
| Элемент          | LTools.SAP.Model.SAPUIItem                                                  | Переменная со ссылкой на элемент управления        |
| Комбо-бокс       | [LTools.SAP.Model.SAPUIComboBox](datatypes/sapuicombobox.md)                | Переменная, хранящая ссылку на комбо-бокс          |
| Таймаут\*        | Int32                                                                       | Предельное время ожидания завершения процесса (мс). По умолчанию `10000` |
| Строгий таймаут  | Boolean                              | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Действия:***  | | |
| Выбрать (ключ)   | String                                                                      | Выбрать значение по ключу                          |
| Выбрать (индекс) | Int32                                                                       | Выбрать значение по индексу                        |
| ***Вывод:***     | | |
| Значение         | [LTools.SAP.Model.SAPUIComboBoxItem](datatypes/sapuicomboboxitem.md)        | Переменная, которая хранит текущее значение комбо-бокса |
| Список           | List <[LTools.SAP.Model.SAPUIComboBoxItem](datatypes/sapuicomboboxitem.md)> | Список значений комбо-бокса                        |
| Переменная       | [LTools.SAP.Model.SAPUIComboBox](datatypes/sapuicombobox.md)                | Переменная для сохранения ссылки на комбо-бокс     |

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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

