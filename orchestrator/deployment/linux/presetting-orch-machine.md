# Предварительная настройка машины Оркестратора
Раздел содержит инструкцию по предварительной настройке машины Оркестратора под CentOS 8.

После установки ОС на машине Оркестратора необходимо выполнить её предварительную настройку. Процесс состоит из нескольких шагов.

### Шаг 1. Установка SSH

В терминале ОС выполняем:
```
# sudo yum install openssh-server
# sudo systemctl start sshd
# sudo systemctl enable sshd
```
Смотрим IP, назначенный машине Оркестратора:
```
# ifconfig
```
Далее по этому IP подключаемся к машине Оркестратора через SSH-клиент, например, [PuTTY](https://putty.org.ru/).

### Шаг 2. Расшаривание папки

Устанавливаем samba:
```
# sudo dnf install samba samba-common samba-client
```
Делаем резервную копию конфигурационного файла:
```
# sudo mv /etc/samba/smb.conf /etc/samba/smb.con.bak
```
Создаем папку:
```
# sudo mkdir -p /srv/samba/shared
```
Назначаем права:
```
# sudo chmod -R 0755 /srv/samba/shared
# sudo chown -R nobody:nobody /srv/samba/shared
# sudo chcon -t samba_share_t /srv/samba/shared
```
Редактируем конфигурационный файл:
```
# sudo vim /etc/samba/smb.conf
```
Вводим в редакторе Vim текст:
```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = centos-8
security = user
map to guest = bad user
dns proxy = no

[Anonymous]
path = /srv/samba/shared
browsable =yes
writable = yes
guest ok = yes
read only = no
```
Сохраняем изменения в smb.conf и закрываем Vim:
```
:wq
```
Проверяем корректность конфигурационного файла:
```
# sudo testparm
```
Открываем файервол:
```
# sudo firewall-cmd --add-service=samba --zone=public --permanent
# sudo firewall-cmd --reload
```
Запускаем службу:
```
# sudo systemctl start smb
# sudo systemctl enable smb
```
Проверяем состояние службы:
```
# sudo systemctl status smb
```
Проверяем доступность папки с другой машины в сети.

### Шаг 3. Копирование дистрибутивов из комплекта поставки
В созданной расшаренной папке создаем папку install, в которую копируем дистрибутивы из комплекта поставки:
```
# md /srv/samba/shared/install
```
Архивы дистрибутивов можно сразу распаковать в одноименные папки.

### Шаг 4. Создание папки для размещения дистрибутивов Робота
```
# md /srv/samba/shared/tmp
```

### Шаг 5. Создание папки для размещения служб Оркестратора
```
# md /opt/Primo
```

### Шаг 6. chmod
Для сервисов Оркестратора LogEventsWebhook, Notifications, States, RobotLogs, WebApi, MachineInfo, Agent, RDP2 возможны указанные ниже модификации для прав на исполняемые файлы и запускаемые скрипты этих сервисов. 

А именно: на файлы Primo.Orchestrator.LogEventsWebhook, Primo.Orchestrator.Notifications,..., Primo.Orchestrator.RDP2: 

```
chmod 777,
chmod 775,
chmod 774,
chmod 771, 
chmod 770, 
chmod 750, 
chmod 740, 
chmod 710, 
chmod 700. 
```
При этом пользователь, запускающий/останавливающий эти сервисы, должен быть:
* либо владельцем (chmod 7XX);
* либо входить в указанную при создании файла группу (chmod 77X);
* либо не существует никаких ограничений по правам пользователя, запускающего соответствующий исполняемый файл/скрипт (chmod 777).
