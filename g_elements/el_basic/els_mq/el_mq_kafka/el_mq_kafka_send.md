# Отправить сообщение Kafka

*Eng: Send message Kafka*

![](<../../../../.gitbook/assets/image (295).png>)

 Компонент используется в RPA-процессах для отправки сообщений в очередь сервера Kafka. Это полезно для интеграции и обмена данными между различными системами и процессами через Kafka — распределённую систему потоковой передачи сообщений. 

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство                       | Тип    | Описание                                           |
| ------------------------------ | ------ | -------------------------------------------------- |
| **SSL**                        |               |  **Функция доступна с версии 1.24.8**                                                                                     |
| Защищенный пароль ключа        | SecureString  | Защищенный пароль для доступа к ключу.                                                    |
| Использовать SSL               | Boolean       | Указывает, следует ли использовать SSL для защищенного соединения.                        |
| Механизм                       | String        | Механизм SASL для аутентификации (например, `PLAIN`, `SCRAM-SHA-256`). Описаны ниже.                  |
| Пароль ключа                   | String        | Пароль для доступа к ключу, используемому для SSL.                                        |
| Проверять сертификат           | Boolean       | Указывает, следует ли проверять достоверность сертификата при установлении соединения.    |
| Протокол                       | String        | Протокол безопасности, используемый для SSL (например, `PLAINTEXT`, `SSL`) Описаны ниже.              |
| Путь к ключу                   | String        | Путь к ключу, который используется для SSL-соединений.                                    |
| Путь к сертификату             | String        | Путь к сертификату, который используется для SSL-соединений.                              |
| Хранилища                      | String        | Хранилища сертификатов, используемые для SSL-соединений.                                  |
| **Сервер**                     |               |                                                                                           |
| Адрес сервера\*                | String        | Адрес сервера Kafka (localhost:9092).                                        |
| Защищенный пароль              | SecureString  | Защищенный пароль для подключения к серверу Kafka.                                        |
| Имя топика/очереди\*           | String        | Имя топика                                          |
| Логин                          | String        | Логин для подключения к серверу Kafka.                                                   |
| Пароль                         | String        | Пароль для подключения к серверу Kafka.                                                  |
| Таймаут\*                      | Int32         | Предельное время ожидания завершения процесса (мс).                          |
| **Сообщение**                  |               |                                                                                           |
| Идемпотентность                | Boolean       | Включение режима идемпотентности для обеспечения уникальности сообщений.  **Функция доступна с версии 1.24.8**                  |
| Отправляемое сообщение (текст) | String        | Текст сообщения, которое необходимо отправить. **Функция доступна с версии 1.24.8**   
| **Общие**                      |               |                                                                                           |
| Наименование                   | String        | Название для действия отправки сообщения, используемое в логах и отчетах.                 |
| Отключить логирование          | Boolean       | Опция отключения логирования при выполнении действия.                                     |
| Пауза до (мс)                  | Integer       | Время задержки перед выполнением действия, указано в миллисекундах.                       |
| Пауза после (мс)               | Integer       | Время задержки после выполнения действия, указано в миллисекундах.                        |
| Продолжить при ошибке          | Boolean       | Указывает, следует ли продолжать выполнение процесса при возникновении ошибки.            |
| Скриншот завершения            | Boolean       | Опция для создания скриншота после завершения действия.                                   |
| Скриншот ошибки                | Boolean       | Опция для создания скриншота в случае возникновения ошибки.                               |                                        

## Механизмы аутентификации в Kafka:

1. GSSAPI (Kerberos)
   -  Использует Kerberos для аутентификации, что является стандартом в крупных корпоративных сетях. GSSAPI предоставляет безопасную и устойчивую аутентификацию, обычно используется в средах, где требуется высокая безопасность. Подробнее на официальном сайте [Kerberos Documentation](https://web.mit.edu/kerberos/)
2. Plain
   -  Использует простой текст для передачи имени пользователя и пароля. Это самый простой и часто используемый метод аутентификации, но он менее безопасен по сравнению с другими механизмами. Используется в сценариях, где SSL уже предоставляет достаточный уровень безопасности для передачи учетных данных.
3. Scram Sha256
   -  Использует механизм SCRAM с хэшированием пароля с использованием алгоритма SHA-256. SCRAM (Salted Challenge Response Authentication Mechanism) предоставляет более безопасную форму аутентификации по сравнению с Plain. Подходит для случаев, когда нужно повысить безопасность при аутентификации, сохраняя при этом простоту настройки. [SCRAM Mechanisms](https://datatracker.ietf.org/doc/html/rfc5802)
4. Scram Sha512
   -  Также использует механизм SCRAM, но с более сильным алгоритмом хэширования SHA-512. Это еще более безопасная версия SCRAM, обеспечивающая высокий уровень защиты паролей. Идеален для сред, где безопасность является приоритетом, и требуется максимальная защита учетных данных.
5. OAuth Bearer
   -  Использует токены OAuth для аутентификации. OAuth Bearer является современным механизмом аутентификации, широко применяемым для авторизации и доступа к ресурсам через RESTful API. Подходит для сценариев, где Kafka используется в облачных средах или где уже развернута система OAuth для управления доступом. Подробнее можно ознакомиться в официальной документации [OAuth 2.0 Authorization Framework](https://datatracker.ietf.org/doc/html/rfc6749)

## Описание протоколов:

1. **Plaintext** — Этот протокол передает данные в открытом виде, без шифрования. Используется для незащищенных соединений.
2. **Ssl** — Обеспечивает шифрование данных через SSL (Secure Sockets Layer). Используется для защиты данных при передаче.
3. **Sasl Plaintext** — Протокол с механизмом аутентификации SASL, но без шифрования. Данные передаются в открытом виде, однако используется аутентификация для обеспечения подлинности пользователей.
4. **Sasl Ssl** — Протокол, сочетающий шифрование данных через SSL и механизм аутентификации SASL. Обеспечивает высокий уровень защиты данных.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.MqApp.Kafka_Send("localhost:9092", "login", "password", "topic", "message", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Network.MqApp.Kafka_Send("localhost:9092", "login", "password", "topic", "message", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Network.MqApp.Kafka_Send("localhost:9092", "login", "password", "topic", "message", 10000);
```
{% endtab %}
{% endtabs %}
