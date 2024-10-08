# Пометить сообщение

![](../../../../.gitbook/assets1/studio-linux-elements-basic/exchange-mark-message-activity.png)

Компонент, делающий пометки на сообщениях электронной почты в MS Exchange.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Тип метки** *[LTools.Office.Model.OMailMarkTypes]* - Тип метки сообщения.
1. **Сообщения\*** *[List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)>]* - Список писем для пометки.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
var version = Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2010;
var url = "url";
var login = "login";
var password = "password";
var domain = "domain";
var russianTimeZone = false;

LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, version, url, login, password, domain, russianTimeZone);

List<LTools.Office.Model.OMailMessage> messages = null;
var markType = LTools.Office.Model.OMailMarkTypes.READ;

app.MarkMail(messages, markType);
```
{% endtab %}

{% tab title="Python" %}
```python
version = Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2010;
url = "url";
login = "login";
password = "password";
domain = "domain";
russianTimeZone = False;

app = LTools.Office.MSExchangeApp.InitSvc(wf, version, url, login, password, domain, russianTimeZone);

messages = None;
markType = LTools.Office.Model.OMailMarkTypes.READ;

app.MarkMail(messages, markType);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var version = Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2010;
var url = "url";
var login = "login";
var password = "password";
var domain = "domain";
var russianTimeZone = false;

var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, version, url, login, password, domain, russianTimeZone);

var messages = Null;
var markType = _lib.LTools.Office.Model.OMailMarkTypes.READ;

app.MarkMail(messages, markType);
```
{% endtab %}
{% endtabs %}
