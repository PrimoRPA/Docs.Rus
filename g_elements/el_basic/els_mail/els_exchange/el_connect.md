# Сервер MS Exchange

![](<../../../../.gitbook/assets/image (366).png>)

Компонент производит подключение к серверу MS Exchange.


## Свойства
Свойства элемента разделены на группы, их название выделено в таблице жирным курсивом.

| Свойство           | Тип                                                  | Описание                                                                     |
| ------------------ | ---------------------------------------------------- | ---------------------------------------------------------------------------- |
| ***Общие***  |  | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Exchange*** |  |  |
| Версия             | Microsoft.Exchange.WebServices. Data.ExchangeVersion | Версия сервера MS Exchange                                                   |
| URL сервера        | String                                               | URL сервера MS Exchange. Пример: `"https://<server>/EWS/Exchange.asmx"`      |
| URL Auto Discovery | String                                               | Укажите email пользователя, чтобы использовать автообнаружение URL для эндпойта веб-служб Exchange (EWS). Пример: `"user1@example.com"`  |
| Домен              | String                                               | Имя домена                                                                   |
| Логин              | String                                               | Имя пользователя                                                             |
| Пароль             | String                                               | Пароль учетной записи Exchange              |
| Защищенный пароль |[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0) | Если используется пароль в зашифрованном виде, укажите его в этом поле. В целях безопасности пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из **Диспетчера учетных данных** (Credential Manager) |
| Российский часовой пояс | Boolean                                         | Настройка предназначена для корректировки времени. Например, в случае, если в русской локализации приложения наблюдается ошибка определения часового пояса  |

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

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
