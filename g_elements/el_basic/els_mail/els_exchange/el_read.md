# Чтение почты

![](<../../../../.gitbook/assets/image (324).png>)

Компонент вычитывает электронную почту из MS Exchange.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                    | Описание                                         |
| -------------------- | ---------------------------------------------------------------------- | ------------------------------------------------ |
| Путь к папке         | String                                                                 | Путь к папке MS Exchange. Пример: `"Inbox"`      |
| Только непрочитанные | Boolean                                                                | Определяет, нужно ли читать только непрочитанные сообщения |
| Кол-во               | Int32                                                                  | Количество читаемых сообщений. По умолчанию `30` |
| Вложения             | Boolean                                                                | Определяет, нужно ли получать вложения из писем  |
| Запрос               | String                                                                 | Текст запроса фильтра  |
| Общий ящик           | String                                                                 | Укажите адрес [общего почтового ящика](https://learn.microsoft.com/ru-ru/exchange/collaboration/shared-mailboxes/shared-mailboxes?view=exchserver-2019), если требуется вычитывать его почту. Пример:  `"info@company.com"` |
| Переменная\*         | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Переменная вывода для сохранения списка полученных писем |

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("Inbox", true, false, 10);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = app.ReadMail("Inbox", True, False, 10)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = app.ReadMail("Inbox", true, false, 10);
```
{% endtab %}
{% endtabs %}



