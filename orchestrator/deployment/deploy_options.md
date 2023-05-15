# Развертывание сервера приложений Оркестратора для Windows 2016 Server

Имеется 2 варианта развертывания WebApi и Front для ОС Windows 2016 Server:

| Вариант развертывания <p>WebApi и Front</p> | Особенности SSO | Инструкция | 
| ------------------------------------ | --------------- | ---------------------------------- |
| WebApi и Front работают под IIS      | Сервер может быть включен в AD или можно использовать keytab-файл | Руководство по установке Nginx под Windows 2016 Server **ССЫЛКА**|
| WebApi – служба Windows, <p>Front – nginx</p> | Только keytab-файл | <p>Руководство по установке LogEventsWebhook под CentOS 8 (**ССЫЛКА**),</p> <p>Руководство по предварительной настройке машины Оркестратора под Windows 2016 Server(**ССЫЛКА**),</p> <p>Руководство по установке Notifications под Windows 2016 Server(**ССЫЛКА**)</p> |

**keytab-файл** – файл, полученный в результате команды ktpass при регистрации Front сервиса в AD.\
Путь к полученному keytab-файлу настраивается в конфигурационном файле WebApi в секции ActiveDirectory в параметре **KerberosKeytabPath**:

```json
"ActiveDirectory": {
  "KerberosKeytabPath": "C:\\Primo\\krb5.keytab",
  "Type": 5,
```
### WebApi и Front работают под IIS

При этом варианте развертывания в конфигурационном файле WebApi в параметре **UseIISIntegration** должно быть установлено значение **true**:

```json
"Assignment": {
  "LockTimeout": 5,
  "ReleaseLockTimeoutPeriod": 60
},
"UseIISIntegration": true,
```
### WebApi – служба Windows,  Front – nginx

При этом варианте развертывания в параметре **UseIISIntegration** должно быть установлено значение **false**.

### Linux

При развертывании под Linux WebApi и nginx устанавливаются как демоны Linux.\
SSO возможно только с использованием keytab-файла.



