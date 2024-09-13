# Установка Nginx 

1. Подключитесь к серверу по SSH с пользователем с правами root. 
1. Установите Nginx одним из способов:
   * через менеджер пакетов apt:
     ```
     # sudo apt install nginx
     ```
   * из пакета поставки:
     ```
     # sudo rpm -i nginx-1.16.0-1.el8.ngx.x86_64.rpm
     ```
1. Включите службу в автозагрузку:
   ```
   # sudo systemctl enable nginx
   ```
1. Откройте порт на файерволе:
   ```
   # sudo ufw allow 44392/tcp
   ```
1. Скопируйте конфигурационный файл и сертификаты из комплекта поставки:
   ```
   # cp /srv/samba/shared/install/nginx/nginx.conf /etc/nginx/nginx.conf
   # cp /srv/samba/shared/install/nginx/cert1.crt/etc/nginx/cert1.crt
   # cp /srv/samba/shared/install/nginx/cert1.rsa /etc/nginx/cert1.rsa
   ```
1. Скорректируйте конфигурационный файл:
   ```
   # vim /etc/nginx/nginx.conf
   ```
1. Перезапустите службу:
   ```
   # systemctl restart nginx
   ```
1. Проверьте состояние службы:
   ```
   # systemctl status nginx
   ```

## Что дальше

Теперь вы можете перейти к установке RabbitMQ на машине сервера.
