# Установка PostgreSQL для Linux

Установка пакетов
1.	Обновить список пакетов:
# sudo apt update
2.	Проверить доступные версии:
# apt policy postgresql
Минимальная поддерживаемая версия – 11.
3.	Установить пакет postgresql старшей доступной версии:
# sudo apt install postgresql
4.	Убедиться, что служба postgresql запустилась:
# systemctl status postgresql
________________________________________
● postgresql.service - PostgreSQL RDBMS
   Loaded: loaded (/lib/systemd/system/postgresql.service; enabled; vendor preset: enabled)
   Active: active (exited) since Fri 2021-09-10 12:48:20 MSK; 1min 26s ago
Main PID: 4338 (code=exited, status=0/SUCCESS)
   Tasks: 0 (limit: 4637)
   Memory: 0B
   CGroup: /system.slice/postgresql.service

Первичная настройка СУБД PostgreSQL 
1.	Выполнить вход в сессию служебного пользователя postgres:
# sudo su - postgres
2.	Установить пароль администратора СУБД:
# psql -c "alter user postgres with password '<указать_пароль>'"
•	Вместо текста <пароль> указать устанавливаемый пароль;
•	Пароль заключается в одинарные кавычки;
•	Вся команда заключается в двойные кавычки.

3.	Добавить пользователя СУБД primo:
# createuser primo
Этот пользователь в дальнейшем будет владельцем БД компонентов Primo.AI.Api.
4.	Добавить пользователю primo права на создание БД:
# psql -c "alter user primo createdb"
5.	Установить пароль тестового пользователя:
# psql -c "alter user primo with password '<указать_пароль>'"
6.	Завершить работу в сессии служебного пользователя postgres:
# exit
7.	Наcтроить удаленный доступ к СУБД, для чего в конфигурационном файле /etc/postgresql/NN/main/postgresql.conf проверить и установить параметр listen_addresses и port. 
listen_addresses = '192.168.1.2'
port = 5432
8.	Если в конфигурацию были внесены изменения, то для того чтобы сделанные изменения вступили в силу перезапустить службу postgresql:
# sudo systemctl restart postgresql
9.	Проверить, к каким сетевым портам и интерфейсам подключена служба postgresql, можно командой:
ss -tunelp | grep uid:`id -u postgres`
________________________________________
tcp     LISTEN   0        1024             192.168.1.2:5432          *:*      uid:107 ino:32947 sk:5
10.	Настроить активные сетевые экраны, разрешив доступ к сетевому порту postgresql (по умолчанию - порт 5432):
# sudo ufw allow 5432/tcp



