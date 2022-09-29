# Удалить сообщения

![](<../../../../.gitbook/assets/image (299).png>)

Компонент, удаляющий сообщения электронной почты в MS Exchange.

| Свойство     | Тип                                                                    | Описание                  |
| ------------ | ---------------------------------------------------------------------- | ------------------------- |
| Тип операции | LTools.Office.Model.OMailDeleteTypes                                   | Тип операции удаления     |
| Сообщения\*  | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Список писем для удаления |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("Inbox", true, false, 10);
app.DeleteMail(msg[0], LTools.Office.Model.OMailDeleteTypes.MoveToDeletedItems);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = app.ReadMail("Inbox", True, False, 10)
app.DeleteMail(msg[0], LTools.Office.Model.OMailDeleteTypes.MoveToDeletedItems)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = app.ReadMail("Inbox", true, false, 10);
app.DeleteMail(msg[0], _lib.LTools.Office.Model.OMailDeleteTypes.MoveToDeletedItems);
```
{% endtab %}
{% endtabs %}

