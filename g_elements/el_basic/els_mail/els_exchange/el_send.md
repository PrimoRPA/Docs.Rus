# Отправить сообщение

![](<../../../../.gitbook/assets/image (262).png>)

Компонент, производящий отправку электронной почты через MS Exchange.

| Свойство      | Тип                                                                        | Описание                       |
| ------------- | -------------------------------------------------------------------------- | ------------------------------ |
| Переменная    | [LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)           | Данные отправляемого сообщения |
| Тело письма   | String                                                                     | Тело отправляемого сообщения   |
| Вложения      | List\<String>                                                              | Пути к файлам вложений письма  |
| Кому          | String                                                                     | Адресат сообщения              |
| Тема          | String                                                                     | Тема сообщения                 |
| Формат        | [Tools.Office.Model.OMailMessage.MailFormats](../datatypes/mailformats.md) | Формат сообщения               |
| Ответить      | [LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)           | Ответить на письмо             |
| Ответить всем | Boolean                                                                    | Ответить всем адресатам        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
LTools.Office.Model.OMailMessage msg = new LTools.Office.Model.OMailMessage() { Subject = "subject", Body = "body" };
app.SendMessage(msg);
app.SendMessage("body", "sendTo", "subject", new List<string>() { "file1" }, LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = LTools.Office.Model.OMailMessage() 
msg.Subject = "subject"
msg.Body = "body"
app.SendMessage(msg)
att = List[String]()
att.Add("file1")
app.SendMessage("body", "sendTo", "subject", att, LTools.Office.Model.OMailMessage.MailFormats.HTML)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = host.newObj(_lib.LTools.Office.Model.OMailMessage); 
msg.Subject = "subject";
msg.Body = "body";
var att = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
att.Add("file1");
app.SendMessage(msg);
app.SendMessage("body", "sendTo", "subject", att, _lib.LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}
{% endtabs %}

