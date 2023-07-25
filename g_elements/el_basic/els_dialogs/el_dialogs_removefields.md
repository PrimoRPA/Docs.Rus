# Удалить поля журнала

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (243).png>)

![](<../../../.gitbook/assets/Удалить поля журнала.png>)

Позволяет удалить дополнительные поля из журнала Робота.

> _Описание общих свойств элемента см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)

| Свойство | Тип  | Описание                                       |
| -------- | ---- | ---------------------------------------------- |
| Поля\*   | List | Массив полей, который нужно удалить из журнала |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.RemoveLogField(wf, new List<string>() { "key" });
```
{% endtab %}

{% tab title="Python" %}
```python
msg = List[String]()
msg.Add("key")
		LTools.Workflow.PrimoApp.RemoveLogField(wf, m
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var msg = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
msg.Add("key");
		_lib.LTools.Workflow.PrimoApp.RemoveLogField(wf, msg);
```
{% endtab %}
{% endtabs %}
