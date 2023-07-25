# Получить письма (POP3)

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (239).png>)

![](<../../../.gitbook/assets/image (419).png>)

Компонент, осуществляющий получение почтовых сообщений по протоколу POP3.

| Свойство            | Тип                                                                       | Описание                                           |
| ------------------- | ------------------------------------------------------------------------- | -------------------------------------------------- |
| Сервер\*            | String                                                                    | Адрес почтового сервера                            |
| Порт\*              | Int32                                                                     | Порт почтового сервера                             |
| Логин\*             | String                                                                    | Логин почтового сервера                            |
| Пароль\*            | String                                                                    | Пароль почтового сервера                           |
| SSL\*               | Boolean                                                                   | Признак использования сервером соединения SSL      |
| Удалять\*           | Boolean                                                                   | Автоматически удалять полученные сообщения         |
| Кол-во\*            | Int32                                                                     | Количество считываемых сообщений                   |
| Получать вложения\* | Boolean                                                                   | Признак получения вложений                         |
| Индексы             | List\<String>                                                             | Массив индексов получаемых сообщений               |
| Письма              | List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)> | Массив сообщений                                   |
| Таймаут\*           | Int32                                                                     | Предельное время ожидания завершения процесса (мс) |
| Результат\*         | List<[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)>  | Массив полученных сообщений                        |

{% tabs %}
{% tab title="C#" %}
```csharp
List<LTools.Network.Model.EMail.MailMessage> mail = LTools.Network.MailApp.POP3Receive(wf, "server", 443, "login", "password", 10, new List<string>() { "id1" }, false, false, false, 10000);
List<LTools.Network.Model.EMail.MailMessage> mail2 = LTools.Network.MailApp.POP3Receive(wf, "server", 443, "login", "password", 10, new List<LTools.Network.Model.EMail.MailMessage>(), false, false, false, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
dt.Add("id1")
dt2 = List[LTools.Network.Model.EMail.MailMessage]()
mail = LTools.Network.MailApp.POP3Receive(wf, "server", 443, "login", "password", 10, dt, False, False, False, 10000)
mail2 = LTools.Network.MailApp.POP3Receive(wf, "server", 443, "login", "password", 10, dt2, False, False, False, 10000);
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("id1");
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.LTools.Network.Model.EMail.MailMessage));
var mail = _lib.LTools.Network.MailApp.POP3Receive(wf, "server", 443, "login", "password", 10, lst, false, false, false, 10000);
var mail2 = _libLTools.Network.MailApp.POP3Receive(wf, "server", 443, "login", "password", 10, lst2, false, false, false, 10000);
```
{% endtab %}
{% endtabs %}
