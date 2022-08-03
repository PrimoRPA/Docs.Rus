# Чтение почты

![](<../../../../.gitbook/assets/image (43).png>)

Компонент, производящий чтение электронной почты из MS Exchange.

| Свойство             | Тип                                                                    | Описание                                         |
| -------------------- | ---------------------------------------------------------------------- | ------------------------------------------------ |
| Путь к папке         | String                                                                 | Путь к папке MS Exchange                         |
| Только непрочитанные | Boolean                                                                | Признак получения только непрочитанных сообщений |
| Кол-во               | Int32                                                                  | Кол-во читаемых сообщений                        |
| Вложения             | Boolean                                                                | Получать вложения                                |
| Переменная\*         | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Переменная для хранения списка писем             |

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



