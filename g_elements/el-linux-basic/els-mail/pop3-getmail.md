---
Description: Receive mail (POP3)
---

# Получить письма (POP3)

![](../../../.gitbook/assets1/studio-linux-elements-basic/receive-mails-pop3-activity.png)

Компонент, осуществляющий получение почтовых сообщений по протоколу POP3.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. 
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Сервер\*** *[String]* - Адрес почтового сервера.
1. **Порт\*** *[Int32]* - Порт почтового сервера.
1. **Логин\*** *[String]* - Логин почтового сервера.
1. **Пароль\*** *[String]* - Пароль почтового сервера.
1. **SSL\*** *[Boolean]* - Признак использования сервером соединения SSL.
1. **Удалять\*** *[Boolean]* - Автоматически удалять полученные сообщения.
1. **Кол-во\*** *[Int32]* - Количество считываемых сообщений.
1. **Получать вложения\*** *[Boolean]* - Признак получения вложений.
1. **Индексы** *[List\<String>]* - Массив индексов получаемых сообщений.
1. **Письма** *[List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)>]* - Массив сообщений.
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).
1. **Результат\*** *[List<[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)>]* - Массив полученных сообщений.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
var server = "server";
var port = 443;
var login = "login";
var password = "password";
var messageCount = 10;
List<LTools.Network.Model.EMail.MailMessage> messages = null;
List<string> messageIds = null;
var isDeleteAfterReceive = false;
var isReadingAttachment = false;
var isSsl = false;
var timeout = 10000;
var useSso = false;
MailKit.Security.SecureSocketOptions sso = MailKit.Security.SecureSocketOptions.Auto;
var ignoreCertificate = false;

List<LTools.Network.Model.EMail.MailMessage> mails = LTools.Network.MailApp.POP3Receive(wf, server, port, login, password, messageCount, messageIds, isDeleteAfterReceive, isReadingAttachment, isSsl, timeout, useSso, sso, ignoreCertificate);

List<LTools.Network.Model.EMail.MailMessage> mails2 = LTools.Network.MailApp.POP3Receive(wf, server, port, login, password, messageCount, messages, isDeleteAfterReceive, isReadingAttachment, isSsl, timeout, useSso, sso, ignoreCertificate);
```
{% endtab %}

{% tab title="Python" %}
```python
server = "server";
port = 443;
login = "login";
password = "password";
messageCount = 10;
messages = None;
messageIds = None;
isDeleteAfterReceive = False;
isReadingAttachment = False;
isSsl = False;
timeout = 10000;
useSso = False;
sso = MailKit.Security.SecureSocketOptions.Auto;
ignoreCertificate = False;

mails = LTools.Network.MailApp.POP3Receive(wf, server, port, login, password, messageCount, messageIds, isDeleteAfterReceive, isReadingAttachment, isSsl, timeout, useSso, sso, ignoreCertificate);

mails2 = LTools.Network.MailApp.POP3Receive(wf, server, port, login, password, messageCount, messages, isDeleteAfterReceive, isReadingAttachment, isSsl, timeout, useSso, sso, ignoreCertificate);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var server = "server";
var port = 443;
var login = "login";
var password = "password";
var messageCount = 10;
List<LTools.Network.Model.EMail.MailMessage> messages = Null;
List<string> messageIds = Null;
var isDeleteAfterReceive = false;
var isReadingAttachment = false;
var isSsl = false;
var timeout = 10000;
var useSso = false;
MailKit.Security.SecureSocketOptions sso = MailKit.Security.SecureSocketOptions.Auto;
var ignoreCertificate = false;

var mails = _lib.LTools.Network.MailApp.POP3Receive(wf, server, port, login, password, messageCount, messageIds, isDeleteAfterReceive, isReadingAttachment, isSsl, timeout, useSso, sso, ignoreCertificate);

var mails2 = _libLTools.Network.MailApp.POP3Receive(wf, server, port, login, password, messageCount, messages, isDeleteAfterReceive, isReadingAttachment, isSsl, timeout, useSso, sso, ignoreCertificate);
```
{% endtab %}
{% endtabs %}
