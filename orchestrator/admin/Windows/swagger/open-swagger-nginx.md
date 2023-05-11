# Открытие Swagger в Nginx под Windows 2016 Server

Swagger – интерактивная документация по API Оркестратора. По умолчанию Swagger доступен только на машине Оркестратора по адресу: http://localhost:5001/swagger/index.html

Для возможности пользоваться им на любой машине в сети организации, не открывая порт 5001 Оркестратора, требуется настроить в Nginx проксирование этого адреса.

Как это сделать:

1. Перейдите в папку `C:\Primo\nginx-1.21.1\conf`.
2. Измените файл **nginx.conf**: добавьте в конец файла секцию для проксирования Swagger:

```
location /swagger/ {
     proxy_pass http://app_server;
     proxy_set_header Host $host;
     proxy_set_header X-Real-IP $remote_addr;
     proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
     proxy_set_header X-Forwarded-Proto https;
   }

```

![](<../../../../.gitbook/assets/swagger-nginx-1.png>)

3\. При помощи cmd перезапустите Nginx:
* Перейдите в папку с установленным Nginx: 
`cd C:\Primo\nginx-1.21.1`
* Выполните команду перезапуска Nginx: 
`nginx -s reload`
* Убедитесь, что Nginx запущен, используя команду: 
`tasklist /fi "imagename eq nginx.exe"`

![](<../../../../.gitbook/assets/swagger-nginx-2.png>)

4\. Проверьте доступность Swagger по адресу: https://{IP}:44392/swagger/index.html 

![](<../../../../.gitbook/assets/swagger-nginx-3.png>)
