---
Description: Move to folder (IMAP)
---

# Переместить в папку (IMAP)

![](../../../.gitbook/assets1/studio-linux-elements-basic/move-to-folder-imap-activity.png)

Элемент перемещает сообщения между папками по протоколу IMAP.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. 
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Сервер**           |                                     |                            |
1. **Сервер\*** *[String]* - Адрес почтового сервера.
1. **Порт\*** *[Int32]* - Порт почтового сервера. По умолчанию `993`.
1. **Логин\*** *[String]* - Логин почтового сервера.
1. **Пароль** *[String]* - Пароль почтового сервера.
1. **Защищенный пароль** *[SecureString]* - Если пароль используется в зашифрованном виде, укажите его в этом поле. Пароль в формате SecureString не хранится в открытом виде. Получить его можно, например, из диспетчера учетных данных Windows (Credential Manager).
1. **Использовать SSO** *[Boolean]* - Определяет, нужно ли использовать Secure Socket Options (SSO) - набор параметров и настроек для безопасной передачи данных через защищенное сокет-соединение. По умолчанию параметр отключен.                                                    
1. **SSO** - Способ указания шифрования, которое должно использоваться для сокет-соединения. Значение учитывается, только если включен параметр «Использовать SSO». В этом случае при подключении к почтовому серверу будет использовано SSO и проигнорировано свойство SSL.
1. **SSL\*** *[Boolean]* - Признак использования сервером соединения SSL.
1. **Игнорировать сертификат** *[Boolean]* - Установка флага отключает проверку SSL-сертификата сервера. По умолчанию сертификат сервера проверяется. **Отключение проверки SSL-сертификата может привести к проблемам информационной безопасности (!)**, поэтому параметр следует использовать только в исключительных случаях, когда невозможно без него обойтись.
1. **Папка источник\*** *[String]* - Папка входящих сообщений. По умолчанию `"Inbox"`.
1. **Папка назначения\*** *[String]* - Папка входящих сообщений.
1. **Идентификаторы** *[List\<String>]* - Массив идентификаторов получаемых сообщений.
1. **Письма** *[List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)>]* - Массив сообщений.
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `10000`.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
var server = "server";
var port = 443;
var login = "login";
var password = "password";
var inbox = "inbox";
var outbox = "outbox";
List<LTools.Network.Model.EMail.MailMessage> messages = null;
List<string> messageIds = null;
var isSsl = false;
var ignoreCertificate = false;
var timeout = 10000;

LTools.Network.MailApp.IMAPMoveToFolder(wf, server, port, login, password, inbox, outbox, messages, isSsl, ignoreCertificate, timeout);

LTools.Network.MailApp.IMAPMoveToFolder(wf, server, port, login, password, inbox, outbox, messageIds, isSsl, ignoreCertificate, timeout);
```
{% endtab %}

{% tab title="Python" %}
```python
server = "server";
port = 443;
login = "login";
password = "password";
inbox = "inbox";
outbox = "outbox";
messages = None;
messageIds = None;
isSsl = False;
ignoreCertificate = False;
timeout = 10000;

LTools.Network.MailApp.IMAPMoveToFolder(wf, server, port, login, password, inbox, outbox, messages, isSsl, ignoreCertificate, timeout);

LTools.Network.MailApp.IMAPMoveToFolder(wf, server, port, login, password, inbox, outbox, messageIds, isSsl, ignoreCertificate, timeout);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var server = "server";
var port = 443;
var login = "login";
var password = "password";
var inbox = "inbox";
var outbox = "outbox";
var messages = Null;
var messageIds = Null;
var isSsl = false;
var ignoreCertificate = false;
var timeout = 10000;

_lib.LTools.Network.MailApp.IMAPMoveToFolder(wf, server, port, login, password, inbox, outbox, messages, isSsl, ignoreCertificate, timeout);

_lib.LTools.Network.MailApp.IMAPMoveToFolder(wf, server, port, login, password, inbox, outbox, messageIds, isSsl, ignoreCertificate, timeout);
```
{% endtab %}
{% endtabs %}
