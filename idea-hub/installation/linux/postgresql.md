# PostgreSQL

Проверяем, установлен ли на целевой машине PostgreSQL:
```
psql –version
```
Если PostgreSQL установлен, и его версия >= 13, то переходим к пункту [Настройка базы данных](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/linux/setting-up-database).

В противном случае производим установку PostgreSQL.

## Установка PostgreSQL

1. Используем команду:
   ```
   sudo apt install postgresql postgresql-contrib
   ```
1. После установки вносим изменения в следующие конфигурационные файлы:
   * `/etc/postgresql/14/main/postgresql.conf` — этот файл меняем только в том случае, если рассматривается возможность подключения к БД Idea Hub по сети.

     Находим строку:
     ```
     listen_addresses = 'localhost'
     ```

     Для того, чтобы сервер БД слушал подключения на всех локальных интерфейсах, меняем значение на:
     ```
     listen_addresses = '*'
     ```

     Для того, чтобы сервер БД слушал подключения на конкретном интерфейсе, пишем:
     ```
     listen_addresses = 'IP-address'
     ```

   * `/etc/postgresql/14/main/pg_hba.conf`

     Вносим следующие изменения в соответствии с политиками безопасности предприятия:
     
     ```local   all             all				md5```

     Позволяет любому пользователю локальной системы подключаться к базе данных "postgres", если он передает правильный пароль.

     ```host    all             all             192.168.12.10/24	md5```

     Позволяет любому пользователю компьютера 192.168.12.10 подключаться к базе данных "postgres", если он передаёт правильный пароль.

1. Далее перезапускаем PostgreSQL:

   ```
   sudo systemctl reastart postgresql
   ```
   ```
   sudo systemctl status postgresql


## Что дальше 

Следующий шаг — [настройка базы данных](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/linux/setting-up-database).
