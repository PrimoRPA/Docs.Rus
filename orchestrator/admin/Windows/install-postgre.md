# Установка PostgreSQL 13
Раздел содержит инструкцию по установке **PostgreSQL 13** под Windows 2016 Server.

**Как установить PostgreSQL 13:**

1\. Распаковываем архив `postgresql-13.4-1-windows.zip в C:\Install`.\
2\. Мышкой щелкаем по файлу `C:\Install\postgresql-13.4-1-windows-x64.exe`.\
3\.	Выбираем **Да** в появившемся окне:

![](<../../../.gitbook/assets/install-nginx-win-1.png>)

4\. В следующем окне выбираем **Далее** (Next):

![](<../../../.gitbook/assets/>)

5\.	В следующем окне нужно выбрать директорию (1), куда будет установлена программа. Оставляем все без изменения и нажимаем **Далее** (2):

![](<../../../.gitbook/assets/>)

6\.	В окне выбора компонентов тоже все оставляем по умолчанию и нажимаем **Далее**:

![](<../../../.gitbook/assets/>)

7\.	В следующем окне прописываем путь `C:\Primo\PostgreSQL\Data` (1), где будут располагаться файлы базы данных Оркестратора и конфигурационные файлы, и нажимаем **Далее** (2):

![](<../../../.gitbook/assets/>)

8\.	В следующем окне вводим пароль (1) и его подтверждение (2) для суперпользователя БД (postgres) и нажимаем **Далее**. В дальнейшем пароль можно будет изменить в PostgreSQL.

![](<../../../.gitbook/assets/>)

9\.	В следующем окне не меняем настройки порта по умолчанию (5432) и нажимаем **Далее**:

![](<../../../.gitbook/assets/>)

10\. Из выпадающего меню (1) выбираем «Русский, Россия» (2) и нажимаем **Далее** (3):

![](<../../../.gitbook/assets/>)

11\. Перепроверяем введенные данные (1). В случае необходимости, можно вернуться, щелкнув «Назад», и исправить параметры. Если все верно, нажимаем **Далее**:

![](<../../../.gitbook/assets/>)

12\. В следующем окне выбираем **Далее**:

![](<../../../.gitbook/assets/>)

13\. Дожидаемся завершения процесса установки:

![](<../../../.gitbook/assets/>)

14\. Stack Builder не понадобится, убираем галочку (1) и нажимаем **Завершить** (2):

![](<../../../.gitbook/assets/>)

15\. Заходим в PostgreSQL через pgAdmin (пользователь postgres/postgres). PgAdmin установится вместе с PostgreSQL и доступен через меню **Пуск**. Требуется для определения параметров оборудования. Если для этого используется сервис MachineInfo, то не нужно.
* Создаем пользователя, под которым будут работать компоненты Оркестратора, и необходимые БД:
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
* В БД ltoolslicense выполняем скрипты из папки C:\Install\ltoolslicense:
  * get_cpu_id.sql
  * get_hdd_id.sql
  * get_host_name.sql

:red_circle: **Важно!**\
**При выполнении скриптов из postgresql-13/ltoolslicense нужно следить, чтобы случайно не внести изменения в текст скрипта. Недопустимо вносить даже не значимые с точки зрения кода скрипта пробелы и пустые строки.
В том числе, если отредактировали скрипт в редакторе, который заменил визуально не наблюдаемые символы конца строки (отличаются для Windows- и Linux-строк).**

16\. Настраиваем доступ к БД по сети (по умолчанию она доступна только локально по localhost):
* Открываем папку C:\Primo\PostgreSQL\Data
* Вносим изменения в файл postgresql.conf:
```
listen_addresses = '*'
```
* Вносим изменения в файл pg_hba.conf:
```
local   all      all                  trust
host    all      all     0.0.0.0/0  	trust
```
* Перезапускаем службу PostgreSQL

:white_check_mark: **Готово**: PostgreSQL успешно установлено.
