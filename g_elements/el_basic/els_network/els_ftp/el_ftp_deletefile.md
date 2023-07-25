# Удалить файл по FTP

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (38).png>)

![](<../../../../.gitbook/assets/Удалить файл по FTP.png>)

Позволяет удалить файл с сервера по протоколу FTP(S).

| Свойство        | Тип    | Описание                                           |
| --------------- | ------ | -------------------------------------------------- |
| Тип протокола\* |        | Выберите тип протокола FTP из выпадающего списка   |
| Адрес\*         | String | Укажите адрес сервера FTP                          |
| Логин           | String | Введите логин для подключения к FTP-серверу        |
| Пароль          | String | Введите пароль, если это требуется                 |
| Путь к файлу\*  | String | Укажите путь к файлу, который требуется удалить    |
| Таймаут\*       | Int32  | Предельное время ожидания завершения процесса (мс) |

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
