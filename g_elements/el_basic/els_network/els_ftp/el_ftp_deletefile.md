# Удалить файл по FTP

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (2) (143).png>)

![](<../../../../.gitbook/assets/Удалить файл по FTP.png>)

Компонент, удаляющий файл с сервера по протоколу FTP(S).

| Свойство       | Тип                              | Описание                                           |
| -------------- | -------------------------------- | -------------------------------------------------- |
| Тип протокола\* |                                 | Тип протокола FTP                                  |
| Адрес\*        | String                           | Адрес сервера FTP                                  |
| Логин          | String                           | Логин                                              |
| Пароль         | String                           | Пароль                                             |
| Путь к файлу\* | String                           | Путь удаления файла                                |
| Таймаут\*      | Int32                            | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.NetworkApp.FTPDeleteFile(wf, LTools.Network.FTP.ProtocolTypes.FTPS, "server", "login", "password", "folder/file.txt");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Network.NetworkApp.FTPDeleteFile(wf, LTools.Network.FTP.ProtocolTypes.FTPS, "server", "login", "password", "folder/file.txt")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Network.NetworkApp.FTPDeleteFile(wf, _lib.LTools.Network.FTP.ProtocolTypes.FTPS, "server", "login", "password", "folder/file.txt")
```
{% endtab %}
{% endtabs %}
