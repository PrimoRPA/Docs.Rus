# Установка RabbitMQ 

## Установка пакетов

Если RabbitMQ был установлен ранее, требуется удалить все очереди.

### Если есть доступ к менеджеру пакетов apt
1. Обновите список пакетов:
   ```
   sudo apt update
   ```
1. Проверьте доступные версии:
   ```
   apt policy rabbitmq-server
   ```
1. Установите пакет `rabbitmq-server` старшей доступной версии:
   ```
   sudo apt install rabbitmq-server
   ```

### Если нет доступа к менеджеру пакетов apt
1. Распакуйте во временную папку архив с конфигурациями и зависимостями RabbitMQ:
    ```
    sudo unzip /srv/samba/shared/install/rabbitmq/debs.zip -d install/rabbitmq
    ```
1. Установите пакеты:
    ```
    sudo dpkg -i install/rabbitmq/*.deb
    ```

### После установки службы
Убедитесь, что служба rabbitmq-server запустилась:
```
systemctl status rabbitmq-server
```

![](<../../../../.gitbook/assets1/primo-ai/install/rabbit/rabbit-1.png>)


## Первичная настройка RabbitMQ

1. Скопируйте конфигурационные файлы и сертификаты из общей папки:
   ```
   cd /etc/rabbitmq
   ```
   ```
   sudo cp /srv/samba/shared/install/rabbitmq/rabbitmq.conf rabbitmq.conf
   ```
   ```
   sudo cp /srv/samba/shared/install/rabbitmq/rabbitmq-env.conf rabbitmq-env.conf
   ```
1. Отредактируйте файлы конфигурации.
   Включите шифрование при необходимости:
   ```
   sudo nano rabbitmq.conf 
   ```
   Укажите адрес, на котором сервис будет прослушивать:
   ```
   sudo nano rabbitmq-env.conf
   ```
   После изменений в конфигурации:
   ```
   systemctl restart rabbitmq-server
   ```
   ```
   systemctl status rabbitmq-server
   ```
1. Смените владельца скопированных файлов:
   ```
   cd /etc/rabbitmq
   ```
   ```
   sudo chown rabbitmq:rabbitmq rabbitmq-env.conf rabbitmq.conf
   ```
1. Откройте файервол:
   ```
   sudo ufw allow 5671/tcp
   ```
1. Добавьте пользователя **primo** (последний аргумент – пароль пользователя):
   ```
   rabbitmqctl add_user primo 'Qwe123!@#'
   ```
1. Назначьте права на конфигурацию, чтение и запись для пользователя **primo**:
   ```
   rabbitmqctl set_permissions primo ".*" ".*" ".*"
   ```

## Что дальше

Теперь вы можете перейти к установке PostgreSQL на машине сервера.
