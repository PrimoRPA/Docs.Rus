# Сохранить сообщение

![](<../../../../.gitbook/assets/image (815).png>)

![](<../../../../.gitbook/assets/Сохранить сообщение Exchange и Outlook.png>)

Позволяет сохранить на диск письмо из электронной почты MS Exchange. Корректно работает только внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_connect).

> *Общие свойства элемента описаны в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements).*

| Свойство       |Тип                                                                           | Описание                                          
| -------------- | ---------------------------------------------------------------------------- | --------------------------------------- |
| Путь\*           | String                                                                     | Путь сохранения файла в формате \*.eml  |             
| Сообщение\*      |[LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)  | Письмо для сохранения, переменная       |   


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "URL", "login", "pass", "domain");
app.SaveMessage(msg, @"C:\file.eml");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "URL", "login", "pass", "domain")
app.SaveMessage(msg, "C:\file.eml")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "URL", "login", "pass", "domain");
app.SaveMessage(msg, "C:\\file.eml");
```
{% endtab %}
{% endtabs %}

