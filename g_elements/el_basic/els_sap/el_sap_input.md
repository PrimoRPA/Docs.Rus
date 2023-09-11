# Ввод текста

![](<../../../.gitbook/assets/image (420).png>)

Вводит текст в выбранный элемент управления. Корректно работает только внутри контейнера SAP.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство    | Тип                        | Описание                                           |
| ----------- | -------------------------- | -------------------------------------------------- |
| Окно        | String                     | Позволяет выбрать окно программы, с которым необходимо работать. Требуется указать заголовок окна |
| ID элемента | String                     | ID элемента                                        |
| Элемент     | LTools.SAP.Model.SAPUIItem | Ссылка на элемент управления                       |
| Текст\*     | String                     | Вводимый текст                                     |
| Таймаут\*   | Int32                      | Предельное время ожидания завершения процесса (мс) |
| Строгий таймаут | Boolean                | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |

## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
app.TypeText("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", "test");
LTools.SAP.Model.SAPUIItem item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", 10000);
app.TypeText(item, "test");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf);
app.TypeText("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", "test")
item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", 10000)
app.TypeText(item, "test")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
app.TypeText("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", "test");
var item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/txtREPORT-LOW", 10000);
app.TypeText(item, "test");
```
{% endtab %}
{% endtabs %}
