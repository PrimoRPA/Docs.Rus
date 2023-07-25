# Получить файл по FTP

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (342).png>)

<figure><img src="../../../../.gitbook/assets/get_file_ftp (1) (1) (1).png" alt=""><figcaption></figcaption></figure>

Компонент, получающий файл от сервера по протоколу FTP(S).

| Свойство        | Тип                              | Описание                                           |
| --------------- | -------------------------------- | -------------------------------------------------- |
| Тип протокола\* | LTools.Network.FTP.ProtocolTypes | Тип протокола FTP                                  |
| Адрес\*         | String                           | Адрес сервера FTP вместе с файлом                  |
| Логин           | String                           | Логин                                              |
| Пароль          | String                           | Пароль                                             |
| Путь к файлу\*  | String                           | Путь сохранения файла                              |
| Таймаут\*       | Int32                            | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.NetworkApp.FTPDowloadFile(wf, LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", "Путь к файлу", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Network.NetworkApp.FTPDowloadFile(wf, LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", "Путь к файлу", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Network.NetworkApp.FTPDowloadFile(wf, _lib.LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", "Путь к файлу", 10000);
```
{% endtab %}
{% endtabs %}
