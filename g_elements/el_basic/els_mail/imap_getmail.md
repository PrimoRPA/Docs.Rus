# Получить письма (IMAP)

*Eng: Receive mail (IMAP)*



![](<../../../.gitbook/assets/image (335).png>)

Элемент используется для получения почтовых сообщений по протоколу IMAP. Cвойства элемента представлены ниже.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство                    | Тип                                                                       | Описание                                               |
| --------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------ |                     
| _**Сервер:**_               |   |  |
| Сервер\*                    | String        | Адрес почтового сервера   |
| Порт\*                      | Int32         | Порт почтового сервера. По умолчанию `993` |
| Логин\*                     | String        | Логин почтового сервера   |
| Пароль                      | String        | Пароль почтового сервера  |
| Защищенный пароль           | SecureString  | При использовании зашифрованного пароля укажите его в этом поле. Пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из Диспетчера учетных данных (Credential Manager) |
| Использовать SSO            | Boolean       | Определяет, нужно ли использовать Secure Socket Options (SSO) - набор параметров и настроек для безопасной передачи данных через защищенное сокет-соединение. По умолчанию параметр отключен. Настройка добавлена в версии 23.11 |                                                        
| SSO                         | -             | Способ указания шифрования, которое должно использоваться для сокет-соединения. Значение учитывается, только если включен параметр «Использовать SSO». В этом случае при подключении к почтовому серверу будет использовано SSO и проигнорировано свойство SSL |
| SSL\*                       | Boolean       | Признак использования сервером соединения SSL  |
| Игнорировать сертификат     | Boolean       | Установка флага отключает проверку SSL-сертификата сервера. По умолчанию сертификат сервера проверяется. **Отключение проверки SSL-сертификата может привести к проблемам информационной безопасности (!)**, поэтому параметр следует использовать только в исключительных случаях, когда невозможно без него обойтись  |
| Папка\*                     | String        | Папка входящих сообщений  |
| Только непрочитанные\*      | Boolean       | Получать только непрочитанные сообщения  |
| Метить, как прочитанные\*   | Boolean       | Автоматически метить полученные сообщения, как прочитанные |
| Метить, как непрочитанные\* | Boolean       | Автоматически метить полученные сообщения, как непрочитанные |
| Дата от\*                   | DateTime?     | Дата начала фильтра сообщений  |
| Дата до\*                   | DateTime?     | Дата окончания фильтра сообщений  |
| Получать вложения\*         | Boolean       | Признак получения вложений  |
| Идентификаторы              | List\<String> | Массив идентификаторов получаемых сообщений |
| Письма                      | List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)> | Массив сообщений |
| Количество                  | Int32         | Количество сообщений   |
| Сортировка                  | -             | Тип сортировки сообщений. По умолчанию установлено значение **Default** - сортировка, используемая на сервере. Возможно выбрать сортировку по дате отправке письма: 1) **By Date Asc** - сортировка по возрастанию даты (от старой к новой); 2) **By Date Desc** - сортировка по убыванию даты (от новой к старой) |     
| Программная сортировка      | Boolean      | Параметр включает сортировку писем на стороне робота. Позволяет использовать сортировку в тех случаях, когда почтовый сервер ее не поддерживает (например, mail.ru). **Ограничение**: не рекомендуем использовать эту функцию при работе с большим количеством писем, например, свыше тысячи. Поскольку для сортировки необходимо считывать все письма из электронного ящика, это может потреблять много оперативной памяти |
| Таймаут\*                   | Int32       | Предельное время ожидания завершения процесса, указывается в миллисекундах. По умолчанию `10000` |
| _**Сообщение:**_            |  |  |
| Результат\*                 | List <[LTools.Network.Model.EMail.MailMessage](datatypes/mailmessage.md)> | Массив полученных сообщений |


### Примечание по использованию сортировки в IMAP:

Чтобы сортировать письма по дате от старых к новым (опция **By Date Asc**), активируйте опцию **Программная сортировка**, установив соответствующий флажок.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
