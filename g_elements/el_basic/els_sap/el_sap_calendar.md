# Календарь

![](<../../../.gitbook/assets/image (287).png>)

Получает указатель на UI-элемент «календарь».

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.\
Символ `?` в типе данных указывает на то, что значение может быть null.

| Свойство          | Тип                                                          | Описание                                           |
| ----------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| ***Процесс***  | | |
| Окно              | String                  | Заголовок окна программы, с которым планируется работать. Для его автоматического заполнения можно использовать инструмент ![](<../../../.gitbook/assets/image (794).png>) - просто наведите им на нужный заголовок |
| ID элемента\*     | String                                                       | ID элемента                                        |
| Элемент           | LTools.SAP.Model.SAPUIItem                                   | Переменная, хранящая ссылку на элемент управления  |
| Календарь         | [LTools.SAP.Model.SAPUICalendar](datatypes/sapuicalendar.md) | Переменная, хранящая ссылку на календарь           |
| Таймаут\*         | Int32                                                        | Предельное время ожидания завершения процесса (мс) |
| Строгий таймаут   | Boolean                              | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Действия***  | | |
| Дата              | DateTime?                                                    | Выбрать дату                                       |
| Диапазон - начало | DateTime?                                                    | Выбрать начало диапазона дат                       |
| Диапазон - конец  | DateTime?                                                    | Выбрать конец диапазона дат                        |
| ***Вывод***  | | |
| Дата              | DateTime?                                                    | Выбранная дата                                     |
| Диапазон - начало | DateTime?                                                    | Выбранное начало диапазона дат                     |
| Диапазон - конец  | DateTime?                                                    | Выбранный конец диапазона дат                      |
| Переменная        | [LTools.SAP.Model.SAPUICalendar](datatypes/sapuicalendar.md) | Переменная для сохранения ссылки на календарь      |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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

