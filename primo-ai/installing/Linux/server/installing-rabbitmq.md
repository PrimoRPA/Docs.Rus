# Установка RabbitMQ 

## Установка пакетов

Если RabbitMQ был установлен ранее, требуется удалить все очереди.

1. Обновить список пакетов:
   ```
   # sudo apt update
   ```
1. Проверить доступные версии:
   ```
   # apt policy rabbitmq-server
   ```
1. Установить пакет rabbitmq-server старшей доступной версии:
   ```
   # sudo apt install rabbitmq-server
   ```
1. Убедиться, что служба rabbitmq-server запустилась:
   ```
   # systemctl status rabbitmq-server
   ```

## Первичная настройка RabbitMQ

1. Скопировать конфигурационные файлы и сертификаты из общей папки:
   ```
   # cd /etc/rabbitmq
   # sudo cp /srv/samba/shared/install/rabbitmq/rabbitmq.conf rabbitmq.conf
   # sudo cp /srv/samba/shared/install/rabbitmq/rabbitmq-env.conf rabbitmq-env.conf
   ```
1. Смена владельца скопированных файлов:
   ```
   # cd /etc/rabbitmq
   # sudo chown rabbitmq:rabbitmq rabbitmq-env.conf rabbitmq.conf
   ```
1. Открытие файерволла:
   ```
   # sudo ufw allow 5671/tcp
   ```
1. Добавление пользователя:
   ```
   # rabbitmqctl add_user primo primo
   ```
1. Назначение прав на чтение и запись для пользователя primo:
   ```
   # rabbitmqctl set_permissions primo "" ".*" ".*"
   ```
