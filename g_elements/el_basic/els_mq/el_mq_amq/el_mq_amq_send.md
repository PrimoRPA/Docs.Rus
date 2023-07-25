# Отправить сообщение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (255).png>)

![](<../../../../.gitbook/assets/image (398).png>)

Компонент, отправляющий сообщение в очередь сервера ActiveMQ.

| Свойство                        | Тип                                 | Описание                                                                          |
| ------------------------------- | ----------------------------------- | --------------------------------------------------------------------------------- |
| Адрес сервера\*                 | String                              | Адрес сервера ActiveMQ (tcp://myserver:61616/)                                    |
| Логин                           | String                              | Логин                                                                             |
| Пароль                          | String                              | Пароль                                                                            |
| Тип назначения\*                | LTools.Network.MQ. DestinationTypes | Тип назначения                                                                    |
| Имя топика/очереди\*            | String                              | Имя топика/очереди                                                                |
| Correlation ID                  | String                              | Correlation ID                                                                    |
| ID группы                       | String                              | ID группы                                                                         |
| Отправляемое сообщение (текст)  | String                              | Отправляемое текстовое сообщение                                                  |
| Отправляемое сообщение (объект) | Object                              | Отправляемый объект                                                               |
| Таймаут\*                       | Int32                               | Предельное время ожидания завершения процесса (мс)                                |
| Использовать Acknowledgement    | Boolean                             | Позволяет использовать режим Acknowledgement                                      |
| Режим Acknowledgement           | -                                   | Если используется режим Acknowledgement, определите его тип из выпадающего списка |
| Добавлять префикс               | Boolean                             | Добавлять префикс к очереди                                                       |
| Быстрый старт                   | Boolean                             | Быстрый старт подключения                                                         |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.MqApp.AMQ_Send(LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", "corrId", "groupId", "message", 10000);
LTools.Network.MqApp.AMQ_Send(LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", "corrId", "groupId", 10, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Network.MqApp.AMQ_Send(LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", "corrId", "groupId", "message", 10000)
LTools.Network.MqApp.AMQ_Send(LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", "corrId", "groupId", 10, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Network.MqApp.AMQ_Send(_lib.LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", "corrId", "groupId", "message", 10000);
_lib.LTools.Network.MqApp.AMQ_Send(_lib.LTools.Network.MQ.DestinationTypes.TOPIC, "tcp://myserver:61616/", "login", "password", "topic", "corrId", "groupId", 10, 10000);
```
{% endtab %}
{% endtabs %}
