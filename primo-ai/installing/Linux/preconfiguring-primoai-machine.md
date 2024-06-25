# Руководство по предварительной настройке машины Primo RPA AI Server под Astra Linux

После установки ОС на машине Primo RPA AI Server необходимо выполнить её предварительную настройку. 

1.	Установка SSH

В терминале ОС выполняем:
```
# sudo apt install openssh-server
# sudo systemctl start ssh
# sudo systemctl enable ssh
```
Смотрим IP, назначенный машине Primo RPA AI Server:

# ifconfig

Далее по этому IP подключаемся к машине Primo RPA AI Server через SSH-клиент, например PuTTY.

2.	Расшаривание папки

Устанавливаем samba:
```
# sudo dnf install samba samba-common samba-client
```

Делаем резервную копию конфига:
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
Редактируем конфиг:
```
# sudo vim /etc/samba/smb.conf
```
Вводим в редакторе vim текст:
 ```
[global]
workgroup = WORKGROUP
server string = Samba Server %v
netbios name = astra
security = user
map to guest = bad user
dns proxy = no

[Anonymous]
path = /srv/samba/shared
browsable =yes
writable = yes
guest ok = yes
read only = no
create mode = 0777
directory mode = 0777
```

Сохраняем изменения в smb.conf и закрываем vim:
```
:wq
```
Проверяем корректность конфига:
```
# sudo testparm
```
Открываем файервол:
```
# sudo ufw allow samba
```
Запускаем службу:
```
# sudo systemctl start smbd
# sudo systemctl enable smbd
```
Проверяем состояние службы:
```
# sudo systemctl status smbd
```
Проверяем доступность папки с другой машины в сети

3.	Копирование дистрибутивов из комплекта поставки

В созданной расшаренной папке создаем папку install, в которую копируем дистрибутивы из комплекта поставки:
```
# mkdir /srv/samba/shared/install
```
	Архивы дистрибутивов можно сразу распаковать в одноименные папки.

4.	Создание папки для размещения служб Primo.AI
```
# mkdir /opt/Primo.AI
```

5.	chmod
Для сервисов Primo.AI.Api: Api, Inference, MachineInfo, Logs, Auth возможны указанные ниже модификации для прав на исполняемые файлы и запускаемые скрипты этих сервисов (т.е. на файлы Primo.AI.Api, Primo.AI.Api.Inference... Primo.AI.Api.Auth):

chmod 777,
chmod 775,
chmod 774,
chmod 771, 
chmod 770, 
chmod 750, 
chmod 740, 
chmod 710, 
chmod 700.

При этом пользователь, запускающий/останавливающий эти сервисы должен быть либо владельцем (chmod 7XX), либо входить в указанную при создании файла группу (chmod 77X), либо никаких ограничений по правам пользователя запускающего соответствующий исполняемый файл/скрипт не существует (chmod 777).


