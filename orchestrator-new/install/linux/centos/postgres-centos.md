# Установка PostgreSQL под CentOS 8

Вместо CentOS 8 можно использовать RHEL 8.4+. Для RHEL 7.9 потребуется использовать yum.

> Если в продуктивной среде предполагаются большие нагрузки, рекомендуется после установки PostgreSQL установить pgbouncer.
Информацию о его установке можно найти в статье [Установка pgbouncer под CentOS 8](../../../../orchestrator-new/install/linux/centos/pgbouncer-centos.md).

Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/).

Инициализируйте БД:

`/usr/pgsql-13/bin/postgresql-13-setup initdb`

Поместите службу в автозапуск:

`systemctl enable --now postgresql-13`

Внесите изменения в файл `postgresql.conf`:
```
vim /var/lib/pgsql/13/data/postgresql.conf

listen_addresses = '*'

:wq
```

Внесите изменения в файл `pg_hba.conf`:
```
vim /var/lib/pgsql/13/data/pg_hba.conf

local    all      all                  	trust

host     all      all     0.0.0.0/0    	trust

:wq

systemctl restart postgresql-13
```
 
Откройте порт PostgreSQL на файерволе:
```
firewall-cmd --zone=public --permanent --add-port 5432/tcp
firewall-cmd --reload
```
