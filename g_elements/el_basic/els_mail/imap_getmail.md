# Получить письма (IMAP)

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (130).png>)

![](<../../../.gitbook/assets/image (335).png>)

Компонент, осуществляющий получение почтовых сообщений по протоколу IMAP.

| Свойство                    | Тип                                                                       | Описание                                                     |
| --------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------ |
| Сервер\*                    | String                                                                    | Адрес почтового сервера                                      |
| Порт\*                      | Int32                                                                     | Порт почтового сервера                                       |
| Логин\*                     | String                                                                    | Логин почтового сервера                                      |
| Пароль\*                    | String                                                                    | Пароль почтового сервера                                     |
| SSL\*                       | Boolean                                                                   | Признак использования сервером соединения SSL                |
| Папка\*                     | String                                                                    | Папка входящих сообщений                                     |
| Только непрочитанные\*      | Boolean                                                                   | Получать только непрочитанные сообщения                      |
| Метить, как прочитанные\*   | Boolean                                                                   | Автоматически метить полученные сообщения, как прочитанные   |
| Метить, как непрочитанные\* | Boolean                                                                   | Автоматически метить полученные сообщения, как непрочитанные |
| Дата от\*                   | DateTime?                                                                 | Дата начала фильтра сообщений                                |
| Дата до\*                   | DateTime?                                                                 | Дата окончания фильтра сообщений                             |
| Получать вложения\*         | Boolean                                                                   | Признак получения вложений                                   |
| Идентификаторы              | List\<String>                                                             | Массив идентификаторов получаемых сообщений                  |
| Письма                      | List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)> | Массив сообщений                                             |
| Таймаут\*                   | Int32                                                                     | Предельное время ожидания завершения процесса (мс)           |
| Результат\*                 | List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)> | Массив полученных сообщений                                  |

{% tabs %}
{% tab title="C#" %}
```csharp
List<LTools.Network.Model.EMail.MailMessage> mail = LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", false, true, false, new List<string>() { "id1" }, DateTime.Now.AddDays(-2), DateTime.Now, false, false, 10000);
List<LTools.Network.Model.EMail.MailMessage> mail2 = LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", false, true, false, new List<LTools.Network.Model.EMail.MailMessage>(), DateTime.Now.AddDays(-2), DateTime.Now, false, false, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
dt.Add("id1")
dt2 = List[LTools.Network.Model.EMail.MailMessage]()
mail = LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", False, True, False, dt, DateTime.Now.AddDays(-2), DateTime.Now, False, False, 10000)
mail2 = LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", False, True, False, dt2, DateTime.Now.AddDays(-2), DateTime.Now, False, False, 10000);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("id1");
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.LTools.Network.Model.EMail.MailMessage));
var mail = _lib.LTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", false, true, false, lst, _lib.DateTime.Now.AddDays(-2), _lib.DateTime.Now, false, false, 10000);
var mail2 = _libLTools.Network.MailApp.IMAPReceive(wf, "server", 443, "login", "password", "inbox", false, true, false, lst2, _lib.DateTime.Now.AddDays(-2), _lib.DateTime.Now, false, false, 10000);
```
{% endtab %}
{% endtabs %}
