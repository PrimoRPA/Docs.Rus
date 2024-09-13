# Предварительная настройка машины Primo RPA AI Server

На машине для Primo RPA AI Server установите ОС Astra Linux. После установки ОС выполните предварительную настройку машины согласно шагам ниже.

## 1. Установка SSH

В терминале ОС выполняем:
```
# sudo apt install openssh-server
# sudo systemctl start ssh
# sudo systemctl enable ssh
```
Смотрим IP, назначенный машине Primo RPA AI Server:
```
# ifconfig
```

Далее по этому IP подключаемся к машине Primo RPA AI Server через SSH-клиент, например PuTTY.


## 2. Создание общей папки

Устанавливаем Samba:
```
# sudo dnf install samba samba-common samba-client
```

Делаем резервную копию конфигурационного файла Samba:
```
# sudo mv /etc/samba/smb.conf /etc/samba/smb.con.bak
```

Создаем общую папку:
```
# sudo mkdir -p /srv/samba/shared
```

Назначаем права доступа к папке:
```
# sudo chmod -R 0755 /srv/samba/shared
# sudo chown -R nobody:nobody /srv/samba/shared
# sudo chcon -t samba_share_t /srv/samba/shared
```

Редактируем конфигурационный файл:
```
# sudo nano /etc/samba/smb.conf
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

Сохраняем изменения в файле `smb.conf` и закрываем vim:
```
:wq
```

Проверяем корректность конфигурационного файла:
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
Проверяем доступность папки с другой машины в сети.


## 3. Копирование дистрибутивов из комплекта поставки

В общей папке `shared` создаем папку `install`:
```
# sudo mkdir /srv/samba/shared/install
```
В папку `install` копируем дистрибутивы из комплекта поставки. Архивы дистрибутивов можно сразу распаковать в одноименные папки.


## 4. Создание папки для служб 

Создаем папку для размещения служб Primo.AI.Api:
```
# sudo mkdir /app/Primo.AI
```

## 5. Настройка прав доступа к службам

Чтобы назначить права на исполняемые файлы и запускаемые скрипты\* служб Primo.AI.Api (Api, Inference, MachineInfo, Logs, Auth), используйте следующие модификации:

chmod 777\
chmod 775\
chmod 774\
chmod 771\
chmod 770

При этом пользователь, запускающий/останавливающий эти службы, должен быть:
* либо владельцем (chmod 7XX);
* либо входить в указанную при создании файла группу (chmod 77X);
* либо не существует ограничений по правам пользователя, запускающего соответствующий исполняемый файл/скрипт (chmod 777).


## 6.	Пользователи и группы

Для работы компонентов API создайте группу пользователей **primo-ai**:
```
# sudo groupadd primo-ai
```
Создайте учетную запись **primo**:
```
# sudo useradd -g primo-ai -m -s /bin/bash primo
```

Установите владельца папки с инсталляцией:
```
# sudo chown -R primo:primo-ai /app/Primo.AI/
```

## Что дальше

Следующий шаг зависит от способа, который вы выбрали для установки компонентов сервера:
* с помощью инсталляторов — см. раздел Установка с инсталлятором.
* вручную — см. раздел Установка Nginx на машине сервера.

>*\*Имеются в виду файлы Primo.AI.Api, Primo.AI.Api.Inference... Primo.AI.Api.Auth*.

