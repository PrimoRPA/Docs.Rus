# Установка States под CentOS 8

Подключитесь к серверу по SSH с пользователем с правами root. 

Скопируйте папку `/srv/samba/shared/install/States` в `/opt/Primo`:

`cp -R  /srv/samba/shared/install/States /opt/Primo`

Создайте службу:

Перейдите в каталог `/opt/Primo/States`

`cd /opt/Primo/States`

Скопируйте файл службы (идет с комплектом поставки) в `/etc/systemd/system`:

```
cp Primo.Orchestrator.States.service /etc/systemd/system/Primo.Orchestrator.States.service
systemctl daemon-reload
```

Поместите службу в автозапуск:
	
`systemctl enable /etc/systemd/system/Primo.Orchestrator.States.service`

Предоставьте права на запуск:

`chmod -R 777 /opt/Primo/States/Primo.Orchestrator.States`

Запустите службу:

`systemctl start Primo.Orchestrator.States`

Проверьте состояние службы:

`systemctl status Primo.Orchestrator.States`

