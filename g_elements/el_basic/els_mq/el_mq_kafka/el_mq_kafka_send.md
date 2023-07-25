# Отправить сообщение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (304).png>)

![](<../../../../.gitbook/assets/image (295).png>)

Компонент, отправляющий сообщение в очередь сервера Kafka.

| Свойство                       | Тип    | Описание                                           |
| ------------------------------ | ------ | -------------------------------------------------- |
| Адрес сервера\*                | String | Адрес сервера Kafka (localhost:9092)               |
| Логин                          | String | Логин                                              |
| Пароль                         | String | Пароль                                             |
| Имя топика\*                   | String | Имя топика                                         |
| Отправляемое сообщение (текст) | String | Отправляемое текстовое сообщение                   |
| Таймаут\*                      | Int32  | Предельное время ожидания завершения процесса (мс) |

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
