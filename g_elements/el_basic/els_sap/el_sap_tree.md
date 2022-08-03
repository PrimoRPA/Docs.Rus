# Дерево

![](<../../../.gitbook/assets/image (87).png>)

Элемент, получающий указатель на UI-элемент Дерево.

| Свойство     | Тип                                                                 | Описание                                           |
| ------------ | ------------------------------------------------------------------- | -------------------------------------------------- |
| ID элемента  | String                                                              | ID элемента                                        |
| Элемент      | LTools.SAP.Model.SAPUIItem                                          | Ссылка на элемент управления                       |
| Дерево       | [LTools.SAP.Model.SAPUITree](datatypes/sapuitree.md)                | Переменная, хранящая ссылку на дерево              |
| Переменная   | [LTools.SAP.Model.SAPUITree](datatypes/sapuitree.md)                | Переменная для сохранения ссылки на дерево         |
| Узлы         | List <[LTools.SAP.Model.SAPUITreeNode](datatypes/sapuitreenode.md)> | Узлы дерева                                        |
| Выбрать      | String                                                              | Выбрать узел дерева                                |
| Двойной клик | String                                                              | Двойной клик узла                                  |
| Развернуть   | String                                                              | Развернуть узел                                    |
| Свернуть     | String                                                              | Свернуть узел                                      |
| Таймаут\*    | Int32                                                               | Предельное время ожидания завершения процесса (мс) |

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

