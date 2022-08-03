# Пометить сообщение

![](<../../../../.gitbook/assets/image (334).png>)

Компонент, делающий пометки на сообщениях электронной почты в MS Exchange.

| Свойство    | Тип                                                                    | Описание                 |
| ----------- | ---------------------------------------------------------------------- | ------------------------ |
| Тип метки   | LTools.Office.Model.OMailMarkTypes                                     | Тип метки сообщения      |
| Сообщения\* | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Список писем для пометки |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("Inbox", true, false, 10);
app.MarkMail(mag[0], LTools.Office.Model.OMailMarkTypes.IMPORTANCE_HIGH);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = app.ReadMail("Inbox", True, False, 10)
app.MarkMail(mag[0], LTools.Office.Model.OMailMarkTypes.IMPORTANCE_HIGH)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = app.ReadMail("Inbox", true, false, 10);
app.MarkMail(mag[0], _lib.LTools.Office.Model.OMailMarkTypes.IMPORTANCE_HIGH);
```
{% endtab %}
{% endtabs %}
