# Чтение почты

![](<../../../../.gitbook/assets/image (324).png>)

Компонент, производящий чтение электронной почты из MS Exchange.

> *Описание общих свойств элемента см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*

| Свойство             | Тип                                                                    | Описание                                         |
| -------------------- | ---------------------------------------------------------------------- | ------------------------------------------------ |
| Путь к папке         | String                                                                 | Путь к папке MS Exchange                         |
| Только непрочитанные | Boolean                                                                | Признак получения только непрочитанных сообщений |
| Кол-во               | Int32                                                                  | Количество читаемых сообщений                    |
| Вложения             | Boolean                                                                | Установите флаг, если нужно получать вложения из писем |
| Запрос               | String                                                                 | Текст запроса фильтра  |
| Общий ящик           | String                                                                 | Укажите адрес [общего почтового ящика](https://learn.microsoft.com/ru-ru/exchange/collaboration/shared-mailboxes/shared-mailboxes?view=exchserver-2019), если требуется вычитывать его почту. Пример:  info@company.com |
| Переменная\*         | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Свойство вывода. Переменная для сохранения списка писем |

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



