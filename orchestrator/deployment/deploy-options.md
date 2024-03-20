# Варианты развертывания сервера приложений 

## Windows Server

Имеется 2 варианта развертывания WebApi и Front для ОС Windows 2016 Server:

| Вариант развертывания WebApi и Front | Особенности SSO | Инструкция | 
| ------------------------------------ | --------------- | ---------------------------------- |
| WebApi и Front работают под IIS      | Сервер может быть включен в AD или можно использовать keytab-файл | См. «Руководство по установке WebApi и UI на IIS под Windows 2016 Server.docx» (входит в поставку) |
| WebApi – служба Windows, <p>Front – Nginx</p> | Только keytab-файл | <p>См. «Руководство по установке WebApi как службы под Windows 2016 Server.docx»;</p> <p>«Руководство по установке UI на nginx под Windows 2016 Server.docx»;</p> <p>«Руководство по установке Nginx под Windows 2016 Server.docx »</p> Все документы входят в поставку |

**keytab-файл** – файл, полученный в результате команды `ktpass` при регистрации Front сервиса в AD.\
Путь к полученному keytab-файлу настраивается в конфигурационном файле WebApi в секции `ActiveDirectory` в параметре `KerberosKeytabPath`:

```json
"ActiveDirectory": {
  "KerberosKeytabPath": "C:\\Primo\\krb5.keytab",
  "Type": 5,
```
### Вариант 1. WebApi и Front работают под IIS

При этом развертывании в конфигурационном файле WebApi в параметре `UseIISIntegration` установите значение `true`:

```json
"Assignment": {
  "LockTimeout": 5,
  "ReleaseLockTimeoutPeriod": 60
},
"UseIISIntegration": true,
```

### Пошаговая инструкция для IIS

См. раздел [Установка Оркестратора на веб-сервер IIS](https://docs.primo-rpa.ru/primo-rpa/orchestrator/quick-installation/iis-web-server).


### Вариант 2. WebApi – служба Windows, Front – Nginx

При этом варианте развертывания в параметре `UseIISIntegration` должно быть установлено значение `false`.

### Пошаговая инструкция для Nginx

См. раздел [Установка Оркестратора на веб-сервер Nginx](https://docs.primo-rpa.ru/primo-rpa/orchestrator/quick-installation/nginx-web-server).


## Linux

При развертывании под Linux WebApi и Nginx устанавливаются как демоны Linux.\
SSO возможно только с использованием keytab-файла.



