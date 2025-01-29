# Развертывание кластера RabbitMQ на CentOS 8.5  

Дополнительная информация по работе с кластерами (на английском языке): [Clustering Guide](https://www.rabbitmq.com/clustering.html) и [Queue Mirroring](https://www.rabbitmq.com/ha.html).

1. На каждом узле кластера развертываем RabbitMQ в соответствии со статьей [Установка RabbitMQ под CentOS 8](../../../../../orchestrator-new/install/linux/centos/rabbitmq-centos.md).

2. На каждом узле кластера открываем дополнительные порты, необходимые для работы кластера:
```
# firewall-cmd --zone=public --add-port=4369/tcp --permanent
# firewall-cmd --reload
```
3. Каждый узел кластера должен иметь уникальное имя хоста. Имя хоста можно задать командой (требуется перезагрузка):
```
# sudo vim /etc/hostname
# sudo reboot
```
Например, для кластера из 2-х узлов с именами хостов node01 и node02 и IP 192.168.1.160 и 192.168.161:

![](../../../../../../orchestrator-new/resources/install/linux/additional-components-linux/HA/rabbit-cluster-1.PNG)

По умолчанию RabbitMQ будет идентифицировать узел как rabbit@hostname.

4. На каждом узле одинаково настраиваем файл /etc/hosts:
```
# sudo vim /etc/hosts
```

![](../../../../../../orchestrator-new/resources/install/linux/additional-components-linux/HA/rabbit-cluster-2.PNG)

![](../../../../../../orchestrator-new/resources/install/linux/additional-components-linux/HA/rabbit-cluster-3.PNG)

5. Настраиваем идентификацию кластера: открываем файл `/var/lib/rabbitmq/.erlang.cookie` на узле node01:
```
# vim /var/lib/rabbitmq/.erlang.cookie
```
и копируем его содержимое в этот же файл на узле node02. Кластер будет образован узлом node01.

6. Останавливаем RabbitMQ на узле node02:
```
# sudo rabbitmqctl stop_app
```
7. Включаем узел node02 в кластер, выполнив на нем команду:
```
# sudo rabbitmqctl join_cluster rabbit@node01
```
8. Запускаем RabbitMQ на узле node02:
```
# sudo rabbitmqctl start_app
```
9. Проверяем состояние кластера на обоих узлах node01 и node02:
```
# sudo rabbitmqctl cluster_status
```

![](../../../../../../orchestrator-new/resources/install/linux/additional-components-linux/HA/rabbit-cluster-4.PNG)

10. Создаем пользователя RabbitMQ для кластера, назначаем ему права. На узле node01 выполняем команды:
```
# sudo rabbitmqctl add_user 'admin' 'Qwe123!@#'
# sudo rabbitmqctl set_user_tags admin administrator
# sudo rabbitmqctl set_permissions -p / admin '.*' '.*' '.*'
```
11. Создаем политику с именем ha-all для репликации типа «реплицируются все очереди на всех узлах». На узле node01 выполняем команду:
```
# sudo rabbitmqctl set_policy ha-all "" '{"ha-mode":"all","ha-sync-mode":"automatic"}'
```
12.	Настраиваем конфиг WebApi appsettings.ProdWin.json на работу с кластером – комментируем секцию Host (или устанавливаем значение null), добавляем IP узлов кластера (или доменные имена, если используются) в секцию Hosts (первым идет IP узла node01):

![](../../../../../../orchestrator-new/resources/install/linux/additional-components-linux/HA/rabbit-cluster-5.PNG)

Типовые проблемы можно диагностировать, проверив статус кластера: 
```
# sudo rabbitmqctl cluster_status
```
Решение проблемы «Network Partitions» (для rabbit@node02):

![](../../../../../../orchestrator-new/resources/install/linux/additional-components-linux/HA/rabbit-cluster-6.PNG)

```
# sudo rabbitmqctl stop_app
# sudo rabbitmqctl reset
# sudo rabbitmqctl join_cluster rabbit@node02
# sudo rabbitmqctl start_app
```