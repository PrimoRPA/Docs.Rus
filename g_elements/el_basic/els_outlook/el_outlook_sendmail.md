# Отправить сообщение

![](<../../../.gitbook/assets/image (73).png>)

Компонент, производящий отправку электронной почты через Outlook. Компонент корректно работает только внутри контейнера Приложение Outlook.

| Свойство       | Тип                                                                                   | Описание                                             |
| -------------- | ------------------------------------------------------------------------------------- | ---------------------------------------------------- |
| Переменная     | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)            | Данные отправляемого сообщения                       |
| Тело письма    | String                                                                                | Тело отправляемого сообщения                         |
| Вложения       | List\<String>                                                                         | Путь к файлу вложения письма                         |
| Кому           | String                                                                                | Адресат сообщения                                    |
| Тема           | String                                                                                | Тема сообщения                                       |
| От кого       | String                                                                     | Отправитель сообщения. Данное поле позволяет изменить отправителя, если это требуется           |
| Имя аккаунта\* | String                                                                                | Имя аккаунта, от которого будет отправлено сообщение |
| Формат         | [LTools.Office.Model.OMailMessage.MailFormats](../els\_mail/datatypes/mailformats.md) | Формат сообщения                                     |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
LTools.Office.Model.OMailMessage msg = new LTools.Office.Model.OMailMessage() { Subject = "subject", Body = "body" };
app.SendMessage(msg, "My");
app.SendMessage("body", "sendTo", "subject", "My", new List<string>() { "file1" }, LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
msg = LTools.Office.Model.OMailMessage() 
msg.Subject = "subject"
msg.Body = "body"
app.SendMessage(msg, "My")
att = List[String]()
att.Add("file1")
app.SendMessage("body", "sendTo", "subject", "My", att, LTools.Office.Model.OMailMessage.MailFormats.HTML)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
var msg = host.newObj(_lib.LTools.Office.Model.OMailMessage); 
msg.Subject = "subject";
msg.Body = "body";
var att = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
att.Add("file1");
app.SendMessage(msg, "My");
app.SendMessage("body", "sendTo", "subject", "My", att, _lib.LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}
{% endtabs %}



