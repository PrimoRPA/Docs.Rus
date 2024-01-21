---
description: Send message
---

# Отправить сообщение

Предназначен для отправки писем через почту MS Exchange. Работает только внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_connect).

![](<../../../../.gitbook/assets/image (262).png>)

Применение элемента позволяет достичь следующих целей:
* сформировать и отправить сообщение;
* ответить на какое-либо сообщение.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа Exchange:** 

1. **Кому\*** *[String]* - адресат сообщения. Обязательный параметр. В случае, если указан только адресат, а все остальные параметры не заполнены, то будет отправлено пустое письмо.
1. **Переменная** *[[LTools.Office.Model.OMailMessage](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailmessage)]* - данные отправляемого сообщения 
1. **Тема** *[String]* - тема сообщения.           
1. **Тело письма** *[String]* - тело отправляемого сообщения. 
1. **Вложения** *[List\<String>]* - пути к файлам вложений письма.     
1. **Кому (в копии)** *[String]* - поставить в копию.
1. **Скрытая копия** *[String]* - поставить в скрытую копию.      
1. **Формат** [Tools.Office.Model.OMailMessage.MailFormats](../datatypes/mailformats.md) - формат сообщения.         
1. **Копировать в папку** *[Boolean]* - копировать сообщение после отправки.
1. **Папка копирования** *[String]* - названия папки для сохранения копии письма. 
1. **От кого** *[String]* - заполняется при необходимости изменить отправителя. В значении укажите почтовый адрес, например: "iv_ivan@mail.ru". При этом адрес должен входить в список разрешенных на почтовом сервере (подробнее см. [здесь](https://docs.microsoft.com/ru-ru/microsoft-365/admin/email/add-another-email-alias-for-a-user?view=o365-worldwide) и [здесь](https://docs.microsoft.com/ru-ru/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user?view=o365-worldwide)). Если значение не задано, то отправителем по умолчанию будет являться владелец учетной записи, под которой осуществляется подключение к серверу MS Exchange.
1. **От имени (отображаемое имя)** *[String]* - отображаемое имя отправителя письма. Используется по желанию и только при условии, если заполнено свойство **От имени (адрес)**. Для указания отображаемого имени необходимо иметь соответствующие права, иначе возникнет ошибка.

**Группа Re:** 

1. **Ответить** *[LTools.Office.Model.OMailMessage]* - название переменной с данными письма, на которое вы хотите ответить. Если одновременно заполнено свойство **Переменная**, то приоритет будет у свойства **Ответить**.  
2. **Ответить всем** *[Boolean]* - если флаг установлен, ответ будет выслан всем адресатам.       



## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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

