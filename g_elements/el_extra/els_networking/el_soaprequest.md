# Запрос SOAP

![](<../../../.gitbook/assets/SOAPRequest.png>)

***Важно!** Элемент доступен только при установке пакета **Primo.Networking**, который скачивается с помощью [Менеджера зависимостей Студии](https://docs.primo-rpa.ru/primo-rpa/primo-studio/projects/manage-dependencies#menedzher-zavisimostei) либо на сайте [NuGet.org](https://www.nuget.org/packages/Primo.Networking).*

Элемент осуществляет базовые виды запросов к сервисам SOAP. Работает на каких ОС?

## Свойства
Все свойства элемента разделены на группы - они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство           | Тип                                                                                | Описание                      |
| ------------------ | ---------------------------------------------------------------------------------- | --------------------------------------------------------- |
| ***Общие***    |  | *Описание общих свойств см. в разделе [Работа с элементами](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)* |
| ***Аутентификация*** |  |  |
| Аутентификация |  -    | Выберите из раскрывающегося списка тип аутентификации. Доступные значения: 1) None - по умолчанию без аутентификации; 2) Simple; 3) Windows; 4) Client Certificate |
| ***Simple***   |  | *Свойства этой группы заполняются, если был выбран тип аутентификации Simple* | 
| Логин          | String                       | Логин  |
| Пароль         | String                       | Пароль |
| Защищенный пароль | [SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=netcore-3.1) | Пароль, зашифрованный с помощью SecureString. Такой пароль не хранится в открытом виде нигде, даже в памяти компьютера. Получить пароль с типом SecureString можно, к примеру, из **Диспетчера учетных данных** (Credential Manager)|
| ***Сертификат*** |  | *Свойства этой группы заполняются, если был выбран тип аутентификации Client Certificate* |
| Сертификат    | String    | Укажите путь к файлу сертификата, либо Subject в хранилище Root |
| Пароль сертификата | String     | Пароль для файла с сертификатом  |
| Защищенный пароль  | [SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=netcore-3.1) | Защищенный пароль сертификата (для файла). Пароль, зашифрованный с помощью SecureString |
| ***SOAP***    |  |  |
| Endpoint\*    | String      | Endpoint сервиса |
| Contract\*    | String      | Contract сервиса |
| Метод\*       | String      | Имя метода       |
| Параметры     | List\<Object\> | Массив параметров метода |
| Тайм-аут:     | Int32       | Тайм-аут запроса (мс). По умолчанию **20000** |
| ***Вывод***   |  |  |
| Заголовки    | [Dictionary](https://learn.microsoft.com/ru-ru/dotnet/api/system.collections.generic.dictionary-2?view=net-5.0)\<string, string\> | Заголовки ответа |
| Ответ         | String      | Ответ сервиса   |

## Окно мастера (wizard)

