# Получить сообщение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (246).png>)

![](<../../../../.gitbook/assets/image (359).png>)

Компонент, получающий сообщения из очереди сервера ActiveMQ.

| Свойство                     | Тип                                                               | Описание                                                  |
| ---------------------------- | ----------------------------------------------------------------- | --------------------------------------------------------- |
| Адрес сервера\*              | String                                                            | Адрес сервера ActiveMQ (tcp://myserver:61616/)            |
| Логин                        | String                                                            | Логин                                                     |
| Пароль                       | String                                                            | Пароль                                                    |
| Тип назначения\*             | LTools.Network.MQ.DestinationTypes                                | Тип назначения                                            |
| Имя очереди/топика\*         | String                                                            | Имя очереди/топика                                        |
| Массив сообщений             | List <[LTools.Network.MQ.AMQMessage](../datatypes/amqmessage.md)> | Массив полученных сообщений                               |
| Удалять сообщения            | Boolean                                                           | Признак удаления сообщений из очереди                     |
| Кол-во                       | Int32                                                             | Количество получаемых сообщений                           |
| ID сообщения                 | String                                                            | ID сообщения в очереди                                    |
| Таймаут\*                    | Int32                                                             | Предельное время ожидания завершения процесса (мс)        |
| Использовать Acknowledgement | Boolean                                                           | Использовать режим Acknowledgement                        |
| Режим Acknowledgement        | -                                                                 | Выберите тип режима Acknowledgement из выпадающего списка |
| Добавлять префикс            | Boolean                                                           | Добавлять префикс к очереди                               |

{% tabs %}
{% tab title="C#" %}
```csharp
List<LTools.Network.MQ.AMQMessage> ret = LTools.Network.MqApp.AMQ_Receive(LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", true, 10000, 10);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Network.MqApp.AMQ_Receive(LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", True, 10000, 10)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Network.MqApp.AMQ_Receive(_lib.LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", true, 10000, 10);
```
{% endtab %}
{% endtabs %}
