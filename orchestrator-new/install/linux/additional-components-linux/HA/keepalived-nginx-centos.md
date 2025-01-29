# Настройка keepalived для nginx на CentOS 8

Отказоустойчивый кластер для nginx можно сделать на основе VRRP. Для этого используем службу **keepalived**.

Пусть имеются 2 сервера nginx (установку и настройку см. в статье ["Установка Nginx под CentOS 8](../../../../../orchestrator-new/install/linux/centos/nginx-centos.md)») c IP (обязательно в одной сети):

192.168.1.165  
192.168.1.167

Будем считать 192.168.1.167 виртуальным IP.

Устанавливаем keepalived (можно установить локально из пакетов, можно через репозиторий из интернет):
```
# yum install keepalived 
# systemctl enable keepalived
# systemctl start keepalived
```
На каждом сервере редактируем keepalived.conf:
```
# vim /etc/keepalived/keepalived.conf
```
Блок global_defs нужен только для настройки рассылки, его можно удалить. `eth0`, если отличается – заменить на свой.

На первом сервере:	
```
! nginx1
global_defs {
    notification_email {
      primo.rpa@mail.ru
    }
    notification_email_from primo.rpa@mail.ru
    smtp_server localhost
    smtp_connect_timeout 30
    ! enable_script_security
    router_id nginx1.primo
}

vrrp_script check_httpstatus {
    script "/opt/scripts/check_httpstatus.sh 127.0.0.1 "
    interval 5
    timeout 150
    weight 100
}

vrrp_instance NGINX_1 {
    state BACKUP
    interface eth0
    virtual_router_id 26
    priority 27
    advert_int 1
    smtp_alert
    authentication {
        auth_type PASS
        auth_pass nginx
    }
    virtual_ipaddress {
        192.168.1.167
    }
    track_script {
        check_httpstatus
    }
}
```
На втором сервере:
```
! nginx2
global_defs {
    notification_email {
      primo.rpa@mail.ru
    }
    notification_email_from primo.rpa@mail.ru
    smtp_server localhost
    smtp_connect_timeout 30
    ! enable_script_security
    router_id nginx2.primo
}

vrrp_script check_httpstatus {
    script "/opt/scripts/check_httpstatus.sh 127.0.0.1"
    interval 5
    timeout 150
    weight 100
}

vrrp_instance NGINX_2 {
    state MASTER
    interface eth0
    virtual_router_id 26
    priority 28
    advert_int 1
    smtp_alert
    authentication {
        auth_type PASS
        auth_pass nginx
    }
    virtual_ipaddress {
        192.168.1.167
    }
    track_script {
        check_httpstatus
    }
}
```
На каждом сервере добавляем разрешающие правила для multicast траффика и VRRP протокола с помощью iptables:
```
# iptables -A INPUT -i eth0 -d 224.0.0.0/8 -j ACCEPT
# iptables -A INPUT -p vrrp -i eth0 -j ACCEPT
```
На каждом сервере создаем скрипт проверки доступности nginx:
```
# mkdir /opt/scripts
# vim /opt/scripts/check_httpstatus.sh

#!/bin/bash
#

ch=$(curl -m 1 -I @${1} -o /dev/null -w '%{http_code}\n' -s)

if [ $ch == 200 ]
then
    exit 0
else
    exit 1
fi
```
Делаем скрипт исполняемым:
```
# sudo chmod +x /opt/scripts/check_httpstatus.sh
```
Перезапускаем keepalived:
```
# systemctl restart keepalived
# systemctl status keepalived
```
Смотрим текущие IP адреса на интерфейсе eth0 серверов:
```
# ip a show eth0
```
Чтобы разрешить nginx слушать на несуществующих IP, включаем в ядре `net.ipv4.ip_nonlocal_bind`:
```
# sudo sysctl -w net.ipv4.ip_nonlocal_bind=1
# sysctl net.ipv4.ip_nonlocal_bind
```
В секции server конфигурационного файла nginx прописываем слушать на обоих IP:
```
# vim /etc/nginx/nginx.conf

server {
    listen 192.168.1.165:80;
    listen 192.168.1.167:80;
…
```
Перезапускаем nginx:
```
# sudo systemctl restart nginx
# sudo systemctl status nginx
```
Проверка кластера сводится к тому, что nginx должен отвечать по адресу 192.168.1.167 (виртуальному IP) при поочередной недоступности серверов 1 и 2.


