# Создать папку FTP

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (38).png>)

![](<../../../../.gitbook/assets/Создать папку FTP.png>)

С помощью этого элемента можно создать папку на FTP-сервере.

| Свойство        | Тип    | Описание                                                                                                                             |
| --------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------ |
| Тип протокола\* |        | Выберите нужный [тип протокола FTP](https://habr.com/ru/post/500438/) из выпадающего списка                                          |
| Адрес\*         | String | Введите адрес FTP-сервера                                                                                                            |
| Логин           | String | Введите логин пользователя для подключения к серверу                                                                                 |
| Пароль          | String | Укажите пароль, если это требуется                                                                                                   |
| Таймаут\*       | Int32  | Предельное время ожидания завершения процесса (мс). Если процесс не был выполнен по истечении таймаута, в консоли отобразится ошибка |
| Путь к папке\*  | String | Укажите путь к папке, которую нужно создать                                                                                          |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Network.NetworkApp.FTPCreateFolder(wf, LTools.Network.FTP.ProtocolTypes.FTPS, "server", "login", "password", "folder/subfolder");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Network.NetworkApp.FTPCreateFolder(wf, LTools.Network.FTP.ProtocolTypes.FTPS, "server", "login", "password", "folder/subfolder")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Network.NetworkApp.FTPCreateFolder(wf, _lib.LTools.Network.FTP.ProtocolTypes.FTPS, "server", "login", "password", "folder/subfolder");
```
{% endtab %}
{% endtabs %}
