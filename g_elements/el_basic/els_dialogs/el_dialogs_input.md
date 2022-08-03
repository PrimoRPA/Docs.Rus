# Диалог ввода

![](<../../../.gitbook/assets/image (415).png>)

Компонент, производящий отображение окна ввода данных.

| Свойство   | Тип           | Описание                                    |
| ---------- | ------------- | ------------------------------------------- |
| Заголовок  | String        | Заголовок диалога ввода                     |
| Текст      | String        | Сопроводительный текст диалога ввода        |
| Справочник | List\<String> | Справочник возможных значений диалога ввода |
| Ширина\*   | Int32         | Ширина отображаемого диалога                |
| Высота\*   | Int32         | Высота отображаемого диалога                |
| Результат  | String        | Полученные от диалога данные                |

{% tabs %}
{% tab title="C#" %}
```csharp
String res = LTools.Workflow.PrimoApp.InputDialog(wf, "title", "text", new List<string>() { "Opt1", "Opt2" }, 200, 100);
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
dt.Add("Opt1")
dt.Add("Opt2")
res = LTools.Workflow.PrimoApp.InputDialog(wf, "title", "text", dt, 200, 100);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();	
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("Opt1");
lst.Add("Opt2");
var res = _lib.LTools.Workflow.PrimoApp.InputDialog(wf, "title", "text", lst, 200, 100);
```
{% endtab %}
{% endtabs %}
