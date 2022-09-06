# Сервер MS Exchange

![](<../../../../.gitbook/assets/image (366).png>)

Компонент, производящий подключение к MS Exchange.

| Свойство           | Тип                                                  | Описание                                                                                       |
| ------------------ | ---------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| Версия             | Microsoft.Exchange.WebServices. Data.ExchangeVersion | Версия сервера MS Exchange                                                                     |
| URL сервера        | String                                               | URL сервера MS Exchange ([https://server/EWS/Exchange.asmx](https://server/EWS/Exchange.asmx)) |
| URL Auto Discovery | String                                               | URL сервиса автопоиска MS Exchange                                                             |
| Домен              | String                                               | Имя домена                                                                                     |
| Логин              | String                                               | Имя пользователя   |
| Пароль             | String                                               | Пароль профиля Outlook |
| Российский часовой пояс | Boolean                                         | Настройка предназначена для корректировки времени. Например, в случае, если в русской локализации приложения наблюдается ошибка определения часового пояса  |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
LTools.Office.MSExchangeApp app2 = LTools.Office.MSExchangeApp.InitAd(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "autodiscovery url", "login", "pass", "domain");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
app2 = LTools.Office.MSExchangeApp.InitAd(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "autodiscovery url", "login", "pass", "domain")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var app = _lib.LTools.Office.MSExchangeApp.InitAd(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "autodiscovery url", "login", "pass", "domain");
```
{% endtab %}
{% endtabs %}
