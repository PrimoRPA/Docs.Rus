# Запись в журнал

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (31).png>)

![](<../../../.gitbook/assets/image (337).png>)

Компонент, производящий запись сообщения в пользовательский журнал.

| Свойство | Тип                         | Описание        |
| -------- | --------------------------- | --------------- |
| Тип\*    | LTools.Enums.LogMessageType | Тип сообщения   |
| Текст\*  | String                      | Текст сообщения |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.AddToLog(wf, "Сообщение", LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Workflow.PrimoApp.AddToLog(wf, "Сообщение", LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, "Сообщение", _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}
