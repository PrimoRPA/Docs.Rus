# Установка PostgreSQL под Windows 2016 Server

1. Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/).

1. Зайдите в PostgreSQL через pgAdmin (пользователь postgres/postgres). pgAdmin установится вместе с PostgreSQL и доступен через меню **ПУСК**.
Требуется для определения параметров оборудования. Если для этого используется сервис MachineInfo, то не нужен.

1. Создайте пользователя, под которым будут работать компоненты Оркестратора, и необходимые БД:
```
CREATE ROLE orch_user WITH
  LOGIN
  NOSUPERUSER
  INHERIT
  NOCREATEDB
  NOCREATEROLE
  NOREPLICATION
  PASSWORD 'postgres';
GRANT pg_execute_server_program TO orch_user;

CREATE DATABASE ltools WITH OWNER orch_user;
CREATE DATABASE ltoolslogs WITH OWNER orch_user;
CREATE DATABASE ltoolsidentity WITH OWNER orch_user;
CREATE DATABASE ltoolslicense WITH OWNER orch_user;
```
4. Настройте доступ к БД по сети (по умолчанию она доступна только локально по localhost):

    * Откройте папку `C:\Primo\PostgreSQL\Data`
    * Внесите изменения в файл postgresql.conf:  
    ```
    listen_addresses = '*'
    ```
    * Внесите изменения в файл pg_hba.conf:
    ```
    local    all      all                  	trust
    host    all      all     0.0.0.0/0  	trust
    ```
5. Перезапустите службу PostgreSQL.



