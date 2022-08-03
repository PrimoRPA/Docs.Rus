# Отправить в буфер обмена

![](<../../../.gitbook/assets/image (66).png>)

Компонент, отправляющий текст в буфер обмена

| Свойство | Тип    | Описание           |
| -------- | ------ | ------------------ |
| Текст    | String | Отправляемый текст |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp.SendToClipboard(wf, "text");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Desktop.DesktopApp.SendToClipboard(wf, "text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Desktop.DesktopApp.SendToClipboard(wf, "text");
```
{% endtab %}
{% endtabs %}

