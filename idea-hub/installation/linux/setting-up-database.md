# Настройка базы данных

Войдем в **psql** под пользователем **postgres**:

```
sudo -i -u postgres
```
```
psql
```

Создадим нового пользователя PostgreSQL, где вместо password требуется указать свой пароль:

```
CREATE USER primo_ideahub WITH PASSWORD 'password';
```

Создадим базу данных и добавим нужные привилегии:
```
CREATE DATABASE ideahub OWNER primo_ideahub;
GRANT ALL PRIVILEGES ON DATABASE ideahub TO primo_ideahub;
CREATE EXTENSION pg_trgm;
```

Выход из psql:
```
postgres=# \q
```

Рестарт сервера:
```
sudo service postgresql restart
```

## Что дальше

Следующий шаг — установка Idea Hub. Начнем с [подготовки к установке](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/drush).
