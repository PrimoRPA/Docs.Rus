# Добавить в очередь

![](<../../../../.gitbook/assets/image (815).png>)

![](<../../../../.gitbook/assets/image (375).png>)

Компонент, производящий запись значения в очередь оркестратора.



| Свойство   | Тип    | Описание                 |
| ---------- | ------ | ------------------------ |
| Очередь\*  | String | Имя очереди              |
| Значение\* | String | Устанавливаемое значение |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.WriteQueue(wf, "queue", "data");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.WriteQueue(wf, "queue", "data")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Enterprise.OrchestratorApp.WriteQueue(wf, "queue", "data");
```
{% endtab %}
{% endtabs %}
