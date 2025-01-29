# Установка RobotLogs под CentOS 8

Подключитесь к серверу по SSH с пользователем с правами root. 

Сначала требуется [установить RabbitMQ](https://azure-dos.s1.primo1.orch/PrimoCollection/Documentation/_git/Documentation.RU?path=/orchestrator-new/install/linux/centos/rabbitmq-centos.md&version=GBOrchestrator-NewDocumentation-InProgress&_a=preview).

Скопируйте папку `/srv/samba/shared/install/RobotLogs-linux` в `/opt/Primo/RobotLogs`:

`cp -R  /srv/samba/shared/install/RobotLogs-linux /opt/Primo/RobotLogs`

Создайте службу:

Перейдите в каталог `/opt/Primo/RobotLogs`

`cd /opt/Primo/RobotLogs`

Скопируйте файл службы (идет с комплектом поставки) в `/etc/systemd/system`:
```
cp Primo.Orchestrator.RobotLogs.service /etc/systemd/system/Primo.Orchestrator.RobotLogs.service
systemctl daemon-reload
```

Поместите службу в автозапуск:
	
`systemctl enable /etc/systemd/system/Primo.Orchestrator.RobotLogs.service`
	
Дайте права на запуск:

`chmod -R 777 /opt/Primo/RobotLogs/Primo.Orchestrator.RobotLogs`

Все остальные настройки выполните аналогично статье [Установка RobotLogs как службы под Windows 2016 Server] (ССЫЫЫЛКА !!!) (файловые пути должны быть в стиле Linux).

Запустите службу:

`systemctl start Primo.Orchestrator.RobotLogs`

Проверьте состояние службы:

`systemctl status Primo.Orchestrator.RobotLogs`

Откройте порт 56748 на файерволе (если служба RobotLogs не на одном сервере с nginx для WebApi):
```
firewall-cmd --zone=public --add-port=56748/tcp --permanent
firewall-cmd --reload
```
