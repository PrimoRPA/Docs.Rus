# Установка Nginx 

Подключаемся к серверу по SSH с пользователем с правами root. 

Устанавливаем Nginx: 
1. Через менеджер пакетов apt:
   ```
   # sudo apt install nginx
   ```
1. Из пакета поставки:
   ```
   # sudo rpm -i nginx-1.16.0-1.el8.ngx.x86_64.rpm
   ```
Включаем службу в автозагрузку:
```
# sudo systemctl enable nginx
```
Открываем порт на файерволе:
 ```
# sudo ufw allow 44392/tcp
```
Копируем конфигурационный файл и сертификаты из комплекта поставки:
```
# cp /srv/samba/shared/install/nginx/nginx.conf /etc/nginx/nginx.conf
# cp /srv/samba/shared/install/nginx/cert1.crt/etc/nginx/cert1.crt
# cp /srv/samba/shared/install/nginx/cert1.rsa /etc/nginx/cert1.rsa
```
При необходимости корректируем конфигурационный файл:
```
# vim /etc/nginx/nginx.conf
```
Перезапускаем службу:
```
# systemctl restart nginx
```
Проверяем состояние службы:
```
# systemctl status nginx
```
	
