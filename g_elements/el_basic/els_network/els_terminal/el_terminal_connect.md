# Присоединиться к серверу

![](<../../../../.gitbook/assets/image (119) (11).png>)

![](<../../../../.gitbook/assets/image (408).png>)

Компонент, осуществляющий подключение к удаленному терминальному серверу

| Свойство   | Тип                    | Описание                                                |
| ---------- | ---------------------- | ------------------------------------------------------- |
| Адрес\*    | String                 | Адрес удаленного сервера                                |
| Порт\*     | Int32                  | Порт удаленного сервера                                 |
| Логин      | String                 | Логин пользователя сервера                              |
| Пароль\*   | String                 | Пароль пользователя сервера                             |
| Переменная | Renci.SshNet.SshClient | Переменная для сохранения ссылки на подключенный сервер |
| Таймаут\*  | Int32                  | Предельное время ожидания соединения (мс)               |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.TServerApp app = LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Network.TServerApp.Init(wf, "address", 22, "login", "pass", 10000);
```
{% endtab %}
{% endtabs %}
