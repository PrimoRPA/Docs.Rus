# Переместить в папку (IMAP)

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (236).png>)

![](<../../../.gitbook/assets/image (427).png>)

Компонент осуществляет перемещение сообщений между папками по протоколу IMAP.

| Свойство           | Тип                                                                       | Описание                                           |
| ------------------ | ------------------------------------------------------------------------- | -------------------------------------------------- |
| ***Общие***        |   | Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements) |
| ***Сервер***       |   |   |
| Сервер\*           | String                                                                    | Адрес почтового сервера                            |
| Порт\*             | Int32                                                                     | Порт почтового сервера                             |
| Логин\*            | String                                                                    | Логин почтового сервера                            |
| Пароль             | String                                                                    | Пароль почтового сервера                           |
| Защищенный пароль  | SecureString  | Если пароль используется в зашифрованном виде, укажите его в этом поле. Пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из Диспетчера учетных данных (Credential Manager) |
| SSL\*              | Boolean                                                                   | Признак использования сервером соединения SSL      |
| Игнорировать сертификат | Boolean                                                              | Установка флага отключает проверку SSL-сертификата сервера. По умолчанию сертификат сервера проверяется. **Отключение проверки SSL-сертификата может привести к проблемам информационной безопасности (!)**, поэтому параметр следует использовать только в исключительных случаях, когда невозможно без него обойтись    |
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
