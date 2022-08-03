# Окно сообщения

![](<../../../.gitbook/assets/image (387).png>)

Компонент, производящий отображение окна с заданным сообщением.

| Свойство | Тип    | Описание               |
| -------- | ------ | ---------------------- |
| Текст\*  | String | Отображаемое сообщение |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.MessageBox(wf, "text");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Workflow.PrimoApp.MessageBox(wf, "text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Workflow.PrimoApp.MessageBox(wf, "text");
```
{% endtab %}
{% endtabs %}
