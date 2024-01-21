---
description: MS Exchange
---

# Сервер MS Exchange

![](<../../../../.gitbook/assets/image (366).png>)

Элемент производит подключение к серверу Microsoft Exchange и позволяет роботу взаимодействовать с ним для выполнения операций с электронной почтой. 

Является контейнером для других элементов, входящих в группу `MS Exchange` (см. рисунок ниже), которые используются для отправки/удаления писем, прикрепления файлов к письмам, извлечения вложений и других операций с электронной почтой.

![](<../../../../.gitbook/assets1/items-from-groups-ms-exchange.png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство           | Тип                                                  | Описание                                                                     |
| ------------------ | ---------------------------------------------------- | ---------------------------------------------------------------------------- |
| ***Exchange:*** |  |  |
| Версия             | Microsoft.Exchange.WebServices. Data.ExchangeVersion | Версия сервера MS Exchange. По умолчанию установлена `Exchange2013_SP1`. Чтобы выбрать другую версию, щелкните выпадающий список значений |
| URL сервера        | String                                               | URL сервера MS Exchange. Пример: `"https://<server>/EWS/Exchange.asmx"`      |
| E-mail             | String                                               | Email пользователя. Укажите его, чтобы использовать [автообнаружение](https://learn.microsoft.com/ru-ru/exchange/architecture/client-access/autodiscover?view=exchserver-2019&viewFallbackFrom=exchserver-2013) URL для эндпойта веб-служб Exchange (EWS). Пример: `"user1@example.com"`  |
| Домен              | String                                               | Имя домена. Пример: `"contoso.com"`                                          |
| Логин              | String                                               | Логин пользователя                                                           |
| Пароль             | String                                               | Пароль учетной записи Exchange                                               |
| Защищенный пароль |[SecureString](https://learn.microsoft.com/ru-ru/dotnet/api/system.security.securestring?view=netcore-2.0) | Поле для вставки зашифрованного пароля. В целях безопасности пароль в формате SecureString не хранится в открытом виде. Получить его можно, например, из программы **Диспетчер учетных данных** (Credential Manager) |
| Российский часовой пояс | Boolean                                         | Настройка предназначена для корректировки времени. Например, в случае, если в русской локализации приложения наблюдается ошибка определения часового пояса. По умолчанию отключено  |

:small_orange_diamond: **Внимание!** Для успешного извлечения вложений из писем необходимо активировать свойство **Российский часовой пояс**.


![](<../../../../.gitbook/assets1/WFAttachExchange.png>)


## Learning
Для обучения работе с элементом **Сервер MS Exchange** скачайте RPA-проект по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).

1. Скачайте архив с обучающими материалами с указанной страницы.
2. Распакуйте архив и откройте проект `StudioActivities` в Студии.
3. Найдите в проекте процесс `StudioActivities/Ru/Почта/MS Exchange/Основы.ltw`. 


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
