# Отправить письмо (SMTP)

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (185).png>)

![](<../../../.gitbook/assets/image (250).png>)

Компонент, осуществляющий отправку почтового сообщения по протоколу SMTP.

| Свойство     | Тип           | Описание                                           |
| ------------ | ------------- | -------------------------------------------------- |
| От\*         | String        | Адресат - От кого                                  |
| Кому\*       | String        | Адресат - Кому                                     |
| Тема         | String        | Тема сообщения                                     |
| Содержимое\* | String        | Содержимое сообщения                               |
| HTML         | Boolean       | Признак HTML-содержимого сообщения                 |
| Вложения     | List\<String> | Пути к файлам вложений                             |
| Сервер\*     | String        | Адрес почтового сервера                            |
| Порт\*       | Int32         | Порт почтового сервера                             |
| Логин\*      | String        | Логин почтового сервера                            |
| Пароль\*     | String        | Пароль почтового сервера                           |
| SSL\*        | Boolean       | Признак использования сервером соединения SSL      |
| Таймаут\*    | Int32         | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.MailApp.SMTPSend(wf, "from", "to", "subject", "body", "server", 443, "login", "password", false, false, new List<string>() { "file1" }, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
dt.Add("file1")
LTools.Network.MailApp.SMTPSend(wf, "from", "to", "subject", "body", "server", 443, "login", "password", False, False, dt, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("file 1");
_lib.LTools.Network.MailApp.SMTPSend(wf, "from", "to", "subject", "body", "server", 443, "login", "password", false, false, lst, 10000);
```
{% endtab %}
{% endtabs %}
