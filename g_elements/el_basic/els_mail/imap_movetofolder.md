# Переместить в папку (IMAP)

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (279).png>)

![](<../../../.gitbook/assets/image (427).png>)

Компонент, осуществляющий перемещение сообщений между папками по протоколу IMAP.

| Свойство           | Тип                                                                       | Описание                                           |
| ------------------ | ------------------------------------------------------------------------- | -------------------------------------------------- |
| Сервер\*           | String                                                                    | Адрес почтового сервера                            |
| Порт\*             | Int32                                                                     | Порт почтового сервера                             |
| Логин\*            | String                                                                    | Логин почтового сервера                            |
| Пароль\*           | String                                                                    | Пароль почтового сервера                           |
| SSL\*              | Boolean                                                                   | Признак использования сервером соединения SSL      |
| Папка источник\*   | String                                                                    | Папка входящих сообщений                           |
| Папка назначения\* | String                                                                    | Папка входящих сообщений                           |
| Идентификаторы     | List\<String>                                                             | Массив идентификаторов получаемых сообщений        |
| Письма             | List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)> | Массив сообщений                                   |
| Таймаут\*          | Int32                                                                     | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
List<LTools.Network.Model.EMail.MailMessage> mail = LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", false, true, false, null, DateTime.Now.AddDays(-2), DateTime.Now, false, false, 10000);
LTools.Network.MailApp.IMAPMoveToFolder(wf, "server", 443, "login", "password", "inbox", "outbox", new List<string>() { mail[0].UID }, false, 10000);
LTools.Network.MailApp.IMAPMoveToFolder(wf, "server", 443, "login", "password", "inbox", "outbox", mail, false, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
mail = LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", False, True, False, null, DateTime.Now.AddDays(-2), DateTime.Now, False, False, 10000)
dt.Add(mail[0].UID)
LTools.Network.MailApp.IMAPMoveToFolder(wf, "server", 443, "login", "password", "inbox", "outbox", dt, False, 10000)
LTools.Network.MailApp.IMAPMoveToFolder(wf, "server", 443, "login", "password", "inbox", "outbox", mail, False, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
var mail = _lib.LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", false, true, false, null, _lib.DateTime.Now.AddDays(-2), _lib.DateTime.Now, false, false, 10000);
lst.Add(mail[0].UID);
_lib.LTools.Network.MailApp.IMAPMoveToFolder(wf, "server", 443, "login", "password", "inbox", "outbox", lst, false, 10000);
_lib.LTools.Network.MailApp.IMAPMoveToFolder(wf, "server", 443, "login", "password", "inbox", "outbox", mail, false, 10000);
```
{% endtab %}
{% endtabs %}
