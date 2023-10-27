# Отправить в буфер обмена
*Eng: Copy to Clipboard*

![](<../../../.gitbook/assets/image (376).png>)

Данный компонент предназначен для отправки текста в буфер обмена

| Свойство | Тип    | Описание                                       |
| -------- | ------ | -----------------------------------------------|
| Текст    | String | Текст, который будет отправлен в буфер обмена  |

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

