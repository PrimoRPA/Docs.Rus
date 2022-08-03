# Звуковой сигнал

![](<../../../.gitbook/assets/image (432).png>)

Компонент, воспроизводящий звук заданной протяженности и частоты.

| Свойство        | Тип   | Описание                             |
| --------------- | ----- | ------------------------------------ |
| Протяженность\* | Int32 | Протяженность звукового сигнала (мс) |
| Частота\*       | Int32 | Частота звукового сигнала (Hz)       |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Workflow.PrimoApp.Beep(wf, 2000, 1000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Workflow.PrimoApp.Beep(wf, 2000, 1000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Workflow.PrimoApp.Beep(wf, 2000, 1000);
```
{% endtab %}
{% endtabs %}
