# Установка PostgreSQL 

## Установка пакетов

1.	Обновите список пакетов:
    ```
    # sudo apt update
    ```
1.	Проверьте доступные версии:
    ```
    # apt policy postgresql
    ```
    Минимальная поддерживаемая версия – 11.

1.	Установите пакет postgresql старшей доступной версии:
    ```
    # sudo apt install postgresql
    ```
1.	Убедитесь, что служба postgresql запустилась:
    ```
    # systemctl status postgresql
    ________________________________________
    ● postgresql.service - PostgreSQL RDBMS
         Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor preset: enabled)
         Active: active (exited) since Fri 2021-09-10 12:48:20 MSK; 1min 26s ago
     Main PID: 4338 (code=exited, status=0/SUCCESS)
         Tasks: 0 (limit: 4637)
         Memory: 0B
         CGroup: /system.slice/postgresql.service

## Первичная настройка СУБД PostgreSQL 

1.	Выполните вход в сессию служебного пользователя **postgres**:
    ```
    # sudo su - postgres
    ```
1.	Установите пароль администратора СУБД:
    ```
    # psql -c "alter user postgres with password '<пароль>'"
    ```
    *	Вместо текста \<пароль\> укажите устанавливаемый пароль;
    *	Пароль заключается в одинарные кавычки;
    *	Вся команда заключается в двойные кавычки.
1.	Добавьте пользователя СУБД **primo**:
    ```
    # createuser primo
    ```
    Этот пользователь в дальнейшем будет владельцем БД компонентов Primo.AI.Api.

1.	Добавьте пользователю **primo** права на создание БД:
    ```
    # psql -c "alter user primo createdb"
    ```
1.	Установите пароль для тестового пользователя:
    ```
    # psql -c "alter user primo with password '<пароль>'"
    ```
1.	Завершите работу в сессии служебного пользователя **postgres**:
    ```
    # exit
    ```
1.	Наcтройте удаленный доступ к СУБД. Для этого в конфигурационном файле `/etc/postgresql/NN/main/postgresql.conf` проверьте и установите параметры **listen_addresses** и **port**. 
    ```
    listen_addresses = '192.168.1.2'
    port = 5432
    ```
1.	Если в конфигурацию были внесены изменения, то для того чтобы они вступили в силу, перезапустите службу postgresql:
    ```
    # sudo systemctl restart postgresql
    ```
1.	Проверьте, к каким сетевым портам и интерфейсам подключена служба postgresql:
    ```
    ss -tunelp | grep uid:`id -u postgres`
    ________________________________________
    tcp     LISTEN   0        1024             192.168.1.2:5432          *:*      uid:107 ino:32947 sk:5
    ```
1.	Настройте активные сетевые экраны, разрешив доступ к сетевому порту postgresql (по умолчанию — порт 5432):
    ```
    # sudo ufw allow 5432/tcp
    ```


## Что дальше

Теперь вы можете перейти к установке компонентов API на машине сервера.
