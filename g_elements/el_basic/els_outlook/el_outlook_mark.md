# Пометить сообщения

![](<../../../.gitbook/assets/image (202).png>)

Компонент, делающий пометки на сообщениях электронной почты в Outlook.

| Свойство    | Тип                                                                              | Описание                 |
| ----------- | -------------------------------------------------------------------------------- | ------------------------ |
| Тип метки   | LTools.Office.Model.OMailMarkTypes                                               | Тип метки сообщения      |
| Сообщения\* | List<[LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)> | Список писем для пометки |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("Inbox", true);
app.MarkMail(msg[0], LTools.Office.Model.OMailMarkTypes.IMPORTANCE_HIGH);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
msg = app.ReadMail("Inbox", True)
app.MarkMail(msg[0], LTools.Office.Model.OMailMarkTypes.IMPORTANCE_HIGH)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
var msg = app.ReadMail("\\имя_профиля\Inbox", true);
app.MarkMail(msg[0], LTools.Office.Model.OMailMarkTypes.IMPORTANCE_HIGH);
```
{% endtab %}
{% endtabs %}
