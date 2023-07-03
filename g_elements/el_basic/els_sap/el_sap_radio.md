# Радио-кнопка

![](<../../../.gitbook/assets/image (400).png>)

Получает указатель на UI-элемент «радио-кнопка».

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство     | Тип                                                                | Описание                                           |
| ------------ | ------------------------------------------------------------------ | -------------------------------------------------- |
| ***Процесс:*** | | |
| Окно         | String                        | Заголовок окна программы, с которым планируется работать. Для его автоматического заполнения можно использовать инструмент ![](<../../../.gitbook/assets/image (794).png>) - просто наведите им на нужный заголовок |
| ID элемента  | String                                                             | ID элемента управления                             |
| Элемент      | LTools.SAP.Model.SAPUIItem                                         | Ссылка на элемент управления                       |
| Радио-кнопка | [LTools.SAP.Model.SAPUIRadioButton](datatypes/sapuiradiobutton.md) | Переменная, хранящая ссылку на радио-кнопку        |
| Таймаут\*    | Int32                                                              | Предельное время ожидания завершения процесса (мс).  По умолчанию **10000** |
| Строгий таймаут | Boolean                 | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Действия:*** | | |
| Выбрать        | Boolean                                                          | Определяет, нужно ли выбрать радио-кнопку          |
| ***Вывод:***    | | |
| Выбрана      | Boolean                                                            | Переменная, которая хранит признак выбранной кнопки |
| Переменная   | [LTools.SAP.Model.SAPUIRadioButton](datatypes/sapuiradiobutton.md) | Переменная для сохранения ссылки на радио-кнопку   |



## Только код
Пример использования элемента в процессе с типом **Только код** (Pure  code):

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
