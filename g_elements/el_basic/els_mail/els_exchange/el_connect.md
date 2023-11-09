# Сервер MS Exchange

![](<../../../../.gitbook/assets/image (366).png>)

Компонент производит подключение к серверу MS Exchange.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство           | Тип                                                  | Описание                                                                     |
| ------------------ | ---------------------------------------------------- | ---------------------------------------------------------------------------- |
| ***Exchange*** |  |  |
| Версия             | Microsoft.Exchange.WebServices. Data.ExchangeVersion | Версия сервера MS Exchange                                                   |
| URL сервера        | String                                               | URL сервера MS Exchange. Пример: `"https://<server>/EWS/Exchange.asmx"`      |
| E-mail             | String                                               | Укажите email пользователя, чтобы использовать автообнаружение URL для эндпойта веб-служб Exchange (EWS). Пример: `"user1@example.com"`  |
| Домен              | String                                               | Имя домена                                                                   |
| Логин              | String                                               | Логин пользователя                                                           |
| Пароль             | String                                               | Пароль учетной записи Exchange                                               |
| Защищенный пароль |[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0) | Если используется пароль в зашифрованном виде, вставьте его в это поле. В целях безопасности пароль в формате SecureString не хранится в открытом виде даже в памяти компьютера. Получить его можно, например, из программы **Диспетчер учетных данных** (Credential Manager) |
| Российский часовой пояс | Boolean                                         | Настройка предназначена для корректировки времени. Например, в случае, если в русской локализации приложения наблюдается ошибка определения часового пояса  |

**Обратите внимание!** Для успешного извлечения вложений необходимо активировать опцию "Российский часовой пояс" в соответствующем поле. В противном случае, при попытке извлечения вложений, возникнет ошибка.

## Обучающий пример
Пример процесса, демонстрирующий основы работы с MS Exchange, можно найти [здесь](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%9F%D0%BE%D1%87%D1%82%D0%B0/MS%20Exchange).


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
