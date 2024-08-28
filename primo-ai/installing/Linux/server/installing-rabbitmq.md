# Установка RabbitMQ 

## Установка пакетов

Если RabbitMQ был установлен ранее, требуется удалить все очереди.

1. Обновите список пакетов:
   ```
   # sudo apt update
   ```
1. Проверьте доступные версии:
   ```
   # apt policy rabbitmq-server
   ```
1. Установите пакет `rabbitmq-server` старшей доступной версии:
   ```
   # sudo apt install rabbitmq-server
   ```
1. Убедитесь, что служба rabbitmq-server запустилась:
   ```
   # systemctl status rabbitmq-server
   ```

   ![](<../../../../.gitbook/assets1/primo-ai/install/rabbit/rabbit-1.png>)


## Первичная настройка RabbitMQ

1. Скопируйте конфигурационные файлы и сертификаты из общей папки:
   ```
   # cd /etc/rabbitmq
   # sudo cp /srv/samba/shared/install/rabbitmq/rabbitmq.conf rabbitmq.conf
   # sudo cp /srv/samba/shared/install/rabbitmq/rabbitmq-env.conf rabbitmq-env.conf
   ```
1. Смените владельца скопированных файлов:
   ```
   # cd /etc/rabbitmq
   # sudo chown rabbitmq:rabbitmq rabbitmq-env.conf rabbitmq.conf
   ```
1. Откройте файервол:
   ```
   # sudo ufw allow 5671/tcp
   ```
1. Добавьте пользователя **primo**:
   ```
   # rabbitmqctl add_user primo primo
   ```
1. Назначьте права на чтение и запись для пользователя **primo**:
   ```
   # rabbitmqctl set_permissions primo "" ".*" ".*"
   ```

## Что дальше

Теперь вы можете перейти к установке PostgreSQL на машине сервера.
