# Всплывающее уведомление

![](<../../../.gitbook/assets/image (885).png>)



Компонент, производящий отображение всплывающего уведомления (Toast Notification) с заданным сообщением.

| Свойство  | Тип     | Описание                        |
| --------- | ------- | ------------------------------- |
| Текст     | String  | Отображаемое сообщение          |
| Заголовок | String  | Заголовок сообщения             |
| Скрывать  | Boolean | Скрывать сообщение при закрытии |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.Toast(wf, "text", "header", false)
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Workflow.PrimoApp.Toast(wf, "text", "header", False)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Workflow.PrimoApp.Toast(wf, "text", "header", false)
```
{% endtab %}
{% endtabs %}
