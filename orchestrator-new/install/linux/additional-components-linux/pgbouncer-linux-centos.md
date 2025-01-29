# Руководство по установке pgbouncer под CentOS 8

## Установка pgbouncer

Для корректной работы pgbouncer на машине должен быть установлен postgresql-server. Если установка производится на той же машине, что и БД, то postgresql-server уже установлен:
```
# yum install -y pgbouncer
```
После выполнения команды проверяем папку /usr/lib/systemd/system/ и ищем в ней файл pgbouncer.service, если файла нет – создаем его. Содержимое файла:
```
[Unit]
Description=A lightweight connection pooler for PostgreSQL
Documentation=man:pgbouncer(1)
After=syslog.target network.target
[Service]
RemainAfterExit=yes
User=postgres
Group=postgres
# Path to the init file
Environment=BOUNCERCONF=/etc/pgbouncer/pgbouncer.ini
ExecStart=/usr/bin/pgbouncer -q ${BOUNCERCONF}
ExecReload=/usr/bin/pgbouncer -R -q ${BOUNCERCONF}
# Give a reasonable amount of time for the server to start up/shut down
TimeoutSec=300
[Install]
WantedBy=multi-user.target
```
Открываем файл /etc/pgbouncer/pgbouncer.ini и редактируем его:
```
[databases]
;; fallback connect string
* = host=10.10.10.35 port=5432 auth_user=postgres
```
Можно не указывать IP, если БД расположена на этом же сервере.
```
[pgbouncer]
logfile = /var/log/pgbouncer/pgbouncer.log
pidfile = /var/run/pgbouncer/pgbouncer.pid
listen_addr = 127.0.0.1, ::1
listen_port = 6432
// listen_addr = * //все адреса 
auth_type = trust
auth_file = /etc/pgbouncer/userlist.txt
admin_users = postgres
stats_users = stats, postgres
pool_mode = transaction
max_client_conn = 100
default_pool_size = 100
```
Открываем файл /etc/pgbouncer/userlist.txt и проверяем,  что там есть строка "postgres" "postgres", если нет – добавляем. 

Для папок /etc/pgbouncer, /var/log/pgbouncer и /var/run/pgbouncer устанавливаем владельца на root и выставляем права на 777 с ключом –R.

Запускаем службу и проверяем ее статус:
```
# systemctl start pgbouncer
# systemctl status pgbouncer
```
Проверяем соединение с БД:
```
# su postgres
# psql -U postgres -h 127.0.0.1 -p 6432 -d ltools
```
Если в качестве listen_addr выбран другой IP, например, внешний, то можно проверить подключение к БД по этому IP.

## Настройка ротации логов с использованием утилиты logrotate

Как правило, утилита logrotate предустановлен во многие дистрибутивы, проверяем есть ли он на машине:
```
# yum list installed
```
Проверяем есть ли запись logrotate:

![]()

Если утилита не установлена, ее необходимо установить:
```
# yum install logrotate
```
![]()

Проверяем, что утилита установлена корректно:
```
# logrotate
```
Редактируем файл /etc/logrotate.conf, основные параметры тут это: rotation-interval, rotation-count and compression. 
По умолчанию интервал выбран weekly (еженедельно), доступны также варианты: hourly, daily, monthly. 
Подробнее о параметрах и допустимых значениях можно уточнить в справочнике утилиты, для этого необходимо выполнить команду:
```
# man logrotate
```
Следующий параметр rotation-count определяет, сколько раз лог-файл будет ротирован перед удалением. Если значение равно 0, то файл сразу удаляется без ротации. 
По умолчанию значение равно 4, то есть, если выбрана ежедневная ротация, то файлы будут храниться максимум 4 дня и потом удаляться.

Сжатие по умолчанию выключено.

Переходим в папку /etc/logrotate.d и ищем там файл конфигурации для ротации логов pgbouncer и редактируем это файл:
```
/var/log/pgbouncer/pgbouncer.log {
    missingok
    notifempty
    sharedscripts
    create 0644 pgbouncer pgbouncer
    nodateext
    daily
    rotate 10
}
```

create 0644 pgbouncer pgbouncer – create mode owner group, группу и владельца можно задать как root,root или другие подходящие.

Таким образом будет создан лог для ежедневной ротации логов pgbouncer и их хранения в течении 10 дней.

Ручная ротация:
```
#logrotate -f /etc/logrotate.conf
```
Проверить статус последней ротации можно в файле /var/lib/logrotate/ logrotate.status, строка с датой последней ротации будет выглядеть примерно так:
```
"/var/log/pgbouncer/pgbouncer.log" 2023-3-2-21:10:25
```

Настройка автоматической ротации логов pgbouncer:

Проверяем, что файл /etc/cron.daily/logrotate содержит строку: `/usr/sbin/logrotate /etc/logrotate.conf`

Если строки нет – ее необходимо дописать.


## Устранение конфликта с внутренним пуллером

При использовании pgbouncer внутренний пуллер необходимо выключить, прописав в коннекшстрин POOLING=False
Иначе возможен конфликт внутреннего пуллера и pgbouncer (внешнего пуллера).
