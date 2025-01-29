# Установка Redis под CentOS 8

Запускаем установку Redis:
```
# yum install redis
```
В появившемся окне подтверждаем установку нажатием кнопки [Y] на клавиатуре.
```
# systemctl enable redis
```
Редактируем файл конфигурации Redis /etc/redis.conf, в нем находим строку 
```
bind 127.0.0.1
```
и меняем IP на внешний IP сервера, например
```
bind 192.168.0.155
```
Сохраняем и закрываем файл.

Перезапускаем службу и проверяем статус:
```
# systemctl restart redis
# systemctl status redis
```
	
Открываем на файерволе порт Redis, используемый по умолчанию, сохраняем конфигурацию и перезагружаем файервол:
```
# firewall-cmd --zone=public --add-port=6379/tcp --permanent
# firewall-cmd --reload
```
Убеждаемся, что порт открыт:
```
# firewall-cmd --list-all
```
Проверяем, что Redis отвечает по указанному IP:
```
# redis-cli -h 192.168.0.155  ping
```
В ответ будет PONG.
	


