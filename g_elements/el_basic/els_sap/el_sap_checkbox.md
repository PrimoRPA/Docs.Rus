# Чек-бокс

![](<../../../.gitbook/assets/image (443).png>)

Получает указатель на UI-элемент «чек-бокс».

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство          | Тип                                                          | Описание                                            |
| ----------------- | ------------------------------------------------------------ | --------------------------------------------------- |
| ***Процесс:*** | | |
| Окно              | String                   | Заголовок окна программы, с которым планируется работать. Для его автоматического заполнения можно использовать инструмент ![](<../../../.gitbook/assets/image (794).png>) - просто наведите им на нужный заголовок |
| ID элемента\*     | String                                                       | ID элемента                                         |
| Элемент           | LTools.SAP.Model.SAPUIItem                                   | Ссылка на элемент управления                        |
| Чек-бокс          | [LTools.SAP.Model.SAPUICheckBox](datatypes/sapuicheckbox.md) | Переменная, хранящая ссылку на чек-бокс             |
| Таймаут\*         | Int32                                                        | Предельное время ожидания завершения процесса (мс). По умолчанию `10000`  |
| Строгий таймаут   | Boolean                 | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Действия:*** | | |
| Сменить состояние | Boolean                                                      | Определяет, нужно ли изменить состояние чек-бокса |
| ***Вывод:***    | | |
| Переменная        | [LTools.SAP.Model.SAPUICheckBox](datatypes/sapuicheckbox.md) | Переменная для сохранения ссылки на чек-бокс        |
| Состояние         | Boolean                                                      | Переменная, которая хранит состояние чек-бокса: включен/выключен |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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

