# Закладки

![](<../../../.gitbook/assets/image (385).png>)

Получает указатель на UI-элемент «закладки».

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство         | Тип                                                          | Описание                                           |
| ---------------- | ------------------------------------------------------------ | -------------------------------------------------- |
| ***Процесс***  | | |
| Окно             | String                     | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента      | String                                                       | ID элемента                                        |
| Элемент          | LTools.SAP.Model.SAPUIItem                                   | Ссылка на элемент управления                       |
| Закладки         | [LTools.SAP.Model.SAPUITabStrip](datatypes/sapuitabstrip.md) | Переменная, хранящая ссылку на закладки            |
| Таймаут\*        | Int32                                                        | Предельное время ожидания завершения процесса (мс) |
| Строгий таймаут  | Boolean                              | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Действия***  | | |
| Выбрать (ключ)   | String                                                       | Выбрать закладку по ключу                          |
| Выбрать (индекс) | Int32                                                        | Выбрать закладку по индексу                        |
| ***Вывод***  | | |
| Переменная       | [LTools.SAP.Model.SAPUITabStrip](datatypes/sapuitabstrip.md) | Переменная для сохранения ссылки на закладки       |
| Элементы         | List<[LTools.SAP.Model.SAPUITab](datatypes/sapuitab.md)>     | Элементы массива закладок                          |


## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUITabStrip tabs = app.TabStrip("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tabs.SelectTab(tabs.Tabs[0].Id);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf);
tabs = app.TabStrip("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
tabs.SelectTab(tabs.Tabs[0].Id)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var tabs = app.TabStrip("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tabs.SelectTab(tabs.Tabs[0].Id);
```
{% endtab %}
{% endtabs %}

