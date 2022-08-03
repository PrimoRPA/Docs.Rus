# Переместить в папку

![](<../../../.gitbook/assets/image (90).png>)

Компонент, осуществляющий перемещение сообщений между папками Outlook.

| Свойство           | Тип                                                                              | Описание                           |
| ------------------ | -------------------------------------------------------------------------------- | ---------------------------------- |
| Папка назначения\* | String                                                                           | Папка назначения (\account\folder) |
| Письма\*           | List<[LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)> | Массив сообщений                   |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("\\имя_профиля\Inbox", true);
app.MoveToFolder(msg[0], "folder");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
msg = app.ReadMail("\\имя_профиля\Inbox", True)
app.MoveToFolder(msg[0], "folder")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
var msg = app.ReadMail("\\имя_профиля\Inbox", true);
app.MoveToFolder(msg[0], "folder");
```
{% endtab %}
{% endtabs %}
