# Дерево

![](<../../../.gitbook/assets/image (308).png>)

С помощью компонента можно получить указатель на UI-элемент «дерево».

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство     | Тип                                                                 | Описание                                           |
| ------------ | ------------------------------------------------------------------- | -------------------------------------------------- |
| ***Процесс***  | | |
| Окно         | String                         | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента  | String                                                              | ID элемента                                        |
| Элемент      | LTools.SAP.Model.SAPUIItem                                          | Ссылка на элемент управления                       |
| Дерево       | [LTools.SAP.Model.SAPUITree](datatypes/sapuitree.md)                | Переменная, хранящая ссылку на дерево              |
| Таймаут\*    | Int32                                                               | Предельное время ожидания завершения процесса (мс) |
| Строгий таймаут | Boolean| Определяет, нужно ли незамедлительно прерывать выполнение элемента по истечении указанного времени в свойстве **Таймаут**. По умолчанию выключено - Робот может продолжать выполнение еще какое-то время, сверх установленного лимита, для полного обхода дерева контролов. На данный момент свойство **введено в тестовом режиме**, поэтому рекомендуется использовать его аккуратно |
| ***Действия***  | | |
| Выбрать      | String                                                              | Выбрать узел дерева                                |
| Двойной клик | String                                                              | Двойной клик узла                                  |
| Клик         | String                                                              | Одиночный клик узла                                |
| Развернуть   | String                                                              | Развернуть узел                                    |
| Свернуть     | String                                                              | Свернуть узел                                      |
| ***Вывод***  | | |
| Переменная   | [LTools.SAP.Model.SAPUITree](datatypes/sapuitree.md)                | Переменная для сохранения ссылки на дерево         |
| Узлы         | List <[LTools.SAP.Model.SAPUITreeNode](datatypes/sapuitreenode.md)> | Узлы дерева                                        |


## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUITree tree = app.Tree("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tree.ExpandNode(tree.Nodes[0].Key);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
tree = app.Tree("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
tree.ExpandNode(tree.Nodes[0].Key)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var tree = app.Tree("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tree.ExpandNode(tree.Nodes[0].Key);
```
{% endtab %}
{% endtabs %}

