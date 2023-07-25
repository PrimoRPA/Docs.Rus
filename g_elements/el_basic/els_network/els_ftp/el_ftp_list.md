# Получить список файлов FTP

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (277).png>)

<figure><img src="../../../../.gitbook/assets/ftp_list_file (1) (1).png" alt=""><figcaption></figcaption></figure>

Компонент, получающий список файлов от сервера по протоколу FTP(S).

| Свойство        | Тип                              | Описание                                           |
| --------------- | -------------------------------- | -------------------------------------------------- |
| Тип протокола\* | LTools.Network.FTP.ProtocolTypes | Тип протокола FTP                                  |
| Адрес\*         | String                           | Адрес сервера FTP                                  |
| Логин           | String                           | Логин                                              |
| Пароль          | String                           | Пароль                                             |
| Переменная\*    | List\<String>                    | Переменная для сохранения результатов              |
| Таймаут\*       | Int32                            | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
List<string> list = LTools.Network.NetworkApp.FTPListFiles(wf, LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
list = LTools.Network.NetworkApp.FTPListFiles(wf, LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var list = _lib.LTools.Network.NetworkApp.FTPListFiles(wf, _lib.LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", 10000);
```
{% endtab %}
{% endtabs %}
