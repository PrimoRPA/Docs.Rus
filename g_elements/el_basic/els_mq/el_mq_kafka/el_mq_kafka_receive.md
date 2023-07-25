# Получить сообщения

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (199).png>)

![](<../../../../.gitbook/assets/image (318).png>)

Компонент, получающий сообщения из очереди сервера Kafka.

| Свойство             | Тип                                                                   | Описание                                              |
| -------------------- | --------------------------------------------------------------------- | ----------------------------------------------------- |
| Адрес сервера\*      | String                                                                | Адрес сервера Kafka (localhost:9092)                  |
| Логин                | String                                                                | Логин                                                 |
| Пароль               | String                                                                | Пароль                                                |
| Имя очереди/топика\* | String                                                                | Имя очереди/топика                                    |
| Group ID             | String                                                                | Group ID                                              |
| Массив сообщений     | List <[LTools.Network.MQ.KafkaMessage](../datatypes/kafkamessage.md)> | Массив полученных сообщений                           |
| Ожидать появление    | Boolean                                                               | Признак ожидания появления нового сообщения в очереди |
| Таймаут\*            | Int32                                                                 | Предельное время ожидания завершения процесса (мс)    |

{% tabs %}
{% tab title="C#" %}
```csharp
List<LTools.Network.MQ.KafkaMessage> ret = LTools.Network.MqApp.Kafka_Receive("localhost:9092", "login", "password", "topic", "groupId", true, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Network.MqApp.Kafka_Receive("localhost:9092", "login", "password", "topic", "groupId", True, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Network.MqApp.Kafka_Receive("localhost:9092", "login", "password", "topic", "groupId", true, 10000);
```
{% endtab %}
{% endtabs %}
