# Отправить файл по FTP

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (12).png>)

![](<../../../../.gitbook/assets/image (437).png>)

Компонент, отправляющий файл на сервер по протоколу FTP(S).

| Свойство       | Тип                              | Описание                                           |
| -------------- | -------------------------------- | -------------------------------------------------- |
| Тип протокола  | LTools.Network.FTP.ProtocolTypes | Тип протокола FTP                                  |
| Адрес\*        | String                           | Адрес сервера FTP                                  |
| Логин          | String                           | Логин                                              |
| Пароль         | String                           | Пароль                                             |
| Путь к файлу\* | String                           | Путь к отправляемому файлу                         |
| Таймаут\*      | Int32                            | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.NetworkApp.FTPUploadFile(wf, LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", "Путь к файлу", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Network.NetworkApp.FTPUploadFile(wf, LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", "Путь к файлу", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Network.NetworkApp.FTPUploadFile(wf, _lib.LTools.Network.FTP.ProtocolTypes.FTP, "server", "login", "pass", "Путь к файлу", 10000);
```
{% endtab %}
{% endtabs %}
