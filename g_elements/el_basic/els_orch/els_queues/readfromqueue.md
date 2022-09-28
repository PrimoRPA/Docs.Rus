# Получить из очереди

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (91).png>)

![](<../../../../.gitbook/assets/image (393).png>)

Компонент, производящий получение значения из очереди оркестратора. В ответе вернется первый элемент очереди.

Свойства

| Свойство  | Тип    | Описание                                  |
| --------- | ------ | ----------------------------------------- |
| Очередь\* | String | Имя очереди                               |
| Результат | String | Переменная для хранения полученных данных |

{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "queue");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "queue")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.PeekQueue(wf, "queue");
```
{% endtab %}
{% endtabs %}
