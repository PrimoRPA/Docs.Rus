# Присутствие элемента

![](<../../../.gitbook/assets/image (290).png>)

Производит поиск элемента управления. Корректно работает только внутри контейнера SAP.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство    | Тип                        | Описание                                             |
| ----------- | -------------------------- | ---------------------------------------------------- |
| ***Процесс:*** | | |
| Окно        | String                     | Окно программы, с которым необходимо работать. Укажите заголовок окна - можете воспользоваться инструментом ![](<../../../.gitbook/assets/image (794).png>) для автоматического заполнения свойства при указании на нужный заголовок |
| ID элемента | String                     | ID элемента управления                               |
| Таймаут\*   | Int32                      | Предельное время ожидания завершения процесса (мс). По умолчанию `10000`   |
| Строгий таймаут | Boolean                | Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Вывод:*** | | |
| Результат   | Boolean                    | Переменная, хранящая результаты поиска               |
| Элемент     | LTools.SAP.Model.SAPUIItem | Переменная, в которой будет храниться ссылка на элемент управления |



## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUIItem item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);
item = app.ElementExists("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
```
{% endtab %}
{% endtabs %}
