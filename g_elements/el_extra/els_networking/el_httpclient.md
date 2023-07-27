# Запрос HTTP

![](<../../../.gitbook/assets/Запрос HTTP.png>)

Создает запрос к конечной точке сервера для получения ответа. Имеет возможности аутентификации, что отличает его от элемента [Запрос WEB-сервиса](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_network/el_webrequest). Поддерживается только на ОС Windows.

**ВАЖНО!** Элемент не является встроенным. Чтобы его использовать, нужно установить пакет Primo.Networking любым из двух способов: 
* при помощи [Менеджера зависимостей Студии](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/manage-dependencies#menedzher-zavisimostei);
* [на сайте NuGet.org](https://www.nuget.org/packages/Primo.Networking).

| Свойство           | Тип                                                                                | Описание                                                  |
| ------------------ | ---------------------------------------------------------------------------------- | --------------------------------------------------------- |
| ***Общие***        |  | Описание общих свойств см. в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements) |
| ***OAuth1***       |  |  |
| Consumer key       | String                                                                             | Consumer key  |
| Consumer secret    | String                                                                             | Consumer secret |
| OAuth1 token       | String                                                                             | OAuth1 token  |
| OAuth1 secret      | String                                                                             | OAuth1 secret |
| ***OAuth2***       |  |  |
| OAuth2 token       | String                                                                             | OAuth2 token  |
| ***Аутентификация сертификата клиента***  |  |  |
| Сертификат клиента     | String                                                                         | Сертификат клиента |
| Пароль сертификата     | String                                                                         | Пароль сертификата |
| Зашифрованный пароль   | [SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=netcore-3.1) | Зашифрованный пароль сертификата. Пароль, зашифрованный с помощью SecureString, не хранится в открытом виде нигде, даже в памяти компьютера. Получить пароль с типом SecureString можно, к примеру, из *Диспетчера учетных данных* (Credential Manager) |
| Проверка SSL           | Boolean  | Установите отметку, если нужно включить проверку сертификата SSL |
| ***Ввод***             |  |  |
| URL\*                  | String      | URL-адрес, на который сделан запрос |
| Метод                  | -           | Выберите метод запроса. По умолчанию GET  |
| Формат                 | -           | Выберите формат ответа, требуемый от сервера. По умолчанию установлен ANY - любой формат |
| ***Вывод***            |  |  |
| Заголовки              | [Dictionary](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0)\<string, string\> | Заголовки ответа |
| Контент                | String          | Контент ответа сервера   |
| Статус                 | Int32           | Статус ответа сервера   |
| ***Параметры запроса***        |  |  |
| Cookies                | [Dictionary](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0)\<string, string\> | Cookies  |
| Вложения               | Dictionary\<string, string\> | Массив путей файлов для загрузки в запрос    |
| Заголовки              | Dictionary\<string, string\> | Заголовки запроса |
| Параметры              | Dictionary\<string, string\> | Параметры запроса |
| Путь к ресурсу         |  String                      | Путь сохранения файла, полученного от запроса   |
| Тело                   |  String                      | Тело запроса. Обращаем внимание, что кавычки в теле запроса необходимо экранировать с помощью символа `\`. Пример экранирования для формата json: `"{\"title\":\"MyTitle\"}"`|
| Формат                 |  String                      | Задайте формат тела. По умолчанию используется XML  |
| Сегменты URL           | Dictionary\<string, string\> | Словарь сегментов, добавляемых к URL. Задаются в формате "{key}" |
| ***Простая проверка подлинности*** |  |  |
| Логин     | String            | Логин |
| Пароль    | String            | Пароль |
| Зашифрованный пароль | [SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=netcore-3.1) | Поле используется для вставки зашифрованного с помощью SecureString пароля |

