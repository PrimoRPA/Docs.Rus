# Отправить сообщение

![](<../../../../.gitbook/assets/image (262).png>)

Предназначен для отправки писем через почту MS Exchange. Работает только внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_connect).

Общие свойства элемента описаны [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements). Утилитарные представлены в таблице ниже. При этом все свойства, кроме **Кому**, являются необязательными. В случае, если указан только адресат, ему будет отправлено пустое письмо.

| Свойство      | Тип                                                                        | Описание                       
| ------------- | -------------------------------------------------------------------------- | ------------------------------ 
| Кому          | String                                                                     | Адресат сообщения. Обязательное поле   
| Переменная    | [LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)           | Данные отправляемого сообщения 
| Тема          | String                                                                     | Тема сообщения                 
| Тело письма   | String                                                                     | Тело отправляемого сообщения   
| Вложения      | List\<String>                                                              | Пути к файлам вложений письма             
| Кому (в копии)| String                                                                     | Поставить в копию             
| Скрытая копия | String                                                                     | Поставить в скрытую копию     
| От кого       | String                                                                     | Заполняется при необходимости изменить отправителя. В значении укажите почтовый адрес, например: "iv_ivan@mail.ru". При этом адрес должен входить в список разрешенных на почтовом сервере (подробнее см. [здесь](https://docs.microsoft.com/ru-ru/microsoft-365/admin/email/add-another-email-alias-for-a-user?view=o365-worldwide) и [здесь](https://docs.microsoft.com/ru-ru/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user?view=o365-worldwide)). Если значение не задано, то отправителем по умолчанию будет являться владелец учетной записи, под которой осуществляется подключение к серверу MS Exchange      
| Формат        | [Tools.Office.Model.OMailMessage.MailFormats](../datatypes/mailformats.md) | Формат сообщения              
| Копировать в папку | Boolean                                                               | Копировать сообщение после отправки 
| Папка копирования  | String                                                                | Названия папки для сохранения копии письма  
| **Группа Re:**    |            |        
| Ответить      | [LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)           | Ответить на письмо             
| Ответить всем | Boolean                                                                    | Если флаг установлен, ответ будет выслан всем адресатам        


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

