# Установка Агента Оркестратора

Руководство содержит инструкции по установке Агента Оркестратора для следующих операционных систем:

* РЕДОС 7.3, 8
* Astra Linux 1.7 
* CentOS 7, 8 

В конце данной статьи вы также можете найти Инструкцию по проверке настройки машины робота.

## Общие настройки

Редактируем конфигурационный файл службы Agent appsettings.ProdLinux.json:

Если в RPA-проекте (zip-архив) присутствуют файлы с кириллицей в наименовании, то для корректной распаковки архива перед запуском робота необходимо, чтобы в конфигурационном файле службы Агента был настроен параметр ProjectZipEncoding. 
Наиболее востребованные значения:  utf-8 (для Windows), cp866 (для Linux) и null (кодировка по умолчанию в ОС):

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-1.PNG)

Настраиваем секцию Orchestrator: 

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-1-1.PNG)

**TenantId** – тенант Агента (для дефолтного тенанта null).


## Действия при установке РЕДОС 7.3, 8

При установке машины робота под управлением РЕДОС 7.3 необходимо:
* на экране **ВЫБОР ПРОГРАММ** отметить базовое окружение **Рабочая станция с графическим окружением (MATE)**

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-3.PNG)

* на экране **СОЗДАНИЕ ПОЛЬЗОВАТЕЛЕЙ** создать пользователя-администратора (далее - primo-admin)

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-4.PNG)

Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.

### Настройка дополнительного ПО

1.	Выполните подключение машины робота к репозиториям base и updates. Настройка локальных зеркал этих репозиториев описана в [Руководстве РЕДОС](https://redos.red-soft.ru/base/server-configuring/service-repositories/create-repo/). 

:large_orange_diamond: **Локальные репозитории необходимо выгружать на машине, имеющей доступ в Интернет.**

Рекомендуется выделить одну машину под управлением РЕДОС 7.3 для размещения на ней сервера репозиториев.

Для машины с доступом в Интернет файл `/etc/yum.repos.d/RedOS-Base.repo` может выглядеть следующим образом:
```
[base]
name=RedOS - Base
baseurl=https://repo1.red-soft.ru/redos/7.3c/$basearch/os,https://mirror.yandex.ru/redos/7.3c/$basearch/os,http://repo.red-soft.ru/redos/7.3c/$basearch/os
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-RED-SOFT
enabled=1
```
а файл `/etc/yum.repos.d/RedOS-Updates.repo` следующим:
```
[updates]
name=RedOS - Updates
baseurl=https://repo1.red-soft.ru/redos/7.3c/$basearch/updates,https://mirror.yandex.ru/redos/7.3c/$basearch/updates,http://repo.red-soft.ru/redos/7.3c/$basearch/updates
gpgcheck=1
gpgkey=file:///etc/pki/rpm-gpg/RPM-GPG-KEY-RED-SOFT
enabled=1
```

2.	Проверьте доступность репозиториев, используя следующую команду:
```
[primo-admin@redos-robot ~]$ sudo dnf repolist
```
Репозитории base и updates должны присутствовать в выводе команды.

3.	Удалите приложения для автообновления ПО (чтобы избежать засорения рабочего стола робота оповещениями):
```
[primo-admin@redos-robot ~]$ sudo dnf -y remove dnfdragora
```
4.	Установите необходимое для работы робота ПО:
```
[primo-admin@redos-robot ~]$ sudo dnf -y install at xorg-x11-server-Xvfb python3-numpy python3-opencv xdotool dotnet-sdk-8.0 ImageMagick
```

### Настройка учетной записи агента

Для работы агента оркестратора и роботов создайте общую группу:
```
[primo-admin@redos-robot ~]$ sudo groupadd primo-rpa
```
Для работы агента оркестратора создайте учётную запись:
```
[primo-admin@redos-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash agent
```
Если требуется, задайте пароль для учётной записи:
```
[primo-admin@redos-robot ~]$ sudo passwd agent
Изменение пароля пользователя agent.
Новый пароль: ***
Повторите ввод нового пароля: ***
passwd: данные аутентификации успешно обновлены.
```

Для запуска агентом оркестратора заданий роботов без прав пользователя root установите следующую настройку:
```
[primo-admin@redos-robot ~]$ sudo sh -c "echo 'agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-rpa-agent"
[primo-admin@redos-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-rpa-agent"
```

### Установка агента

Разворачивание файлов агента оркестратора на машине роботов (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@redos-robot ~]$ sudo mkdir -p /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@redos-robot ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent
[primo-admin@redos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
[primo-admin@redos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@redos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
Установите агент оркестратора как службу и настройте автозапуск:
[primo-admin@redos-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@redos-robot ~]$ sudo systemctl daemon-reload
[primo-admin@redos-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```
В конфигурационном файле appsettings.ProdLinux.json укажите адрес Оркестратора и TenantId (если эта машина не в тенанте по умолчанию) и пользователя из тенанта, а также адрес машины робота:
```
  "Orchestrator": {
    "UserName": "agent",
    "Password": "Qwe123!@#",
    "BaseUrl": "https://192.168.1.154:5001",
    "DownloadRpaProject": true,
    "UserBaseUrlFromRequest": true,
    "TenantId": ""
  },
  ...
  "Agent": {
    ...
    "IpAddress": "192.168.0.20",
    ...
  },
```
Убедитесь, что в конфигурационном файле appsettings.ProdLinux.json правильно указаны команды, с помощью которых агент запускает роботов и управляет машиной (здесь указаны правильные команды для РЕДОС 7.3):
```
  "AgentCommands": {
    "At": "/usr/bin/at",
    "Reboot": "/usr/sbin/reboot",
    "Xvfb": "/usr/bin/xvfb-run",
    "Session": "/usr/bin/mate-session"
  },
```

Запуск службы:
```
[primo-admin@redos-robot ~]$ sudo systemctl start Primo.Orchestrator.Agent
```
Просмотр статуса службы:
```
[primo-admin@redos-robot ~]$ sudo systemctl status Primo.Orchestrator.Agent
```
Просмотр журнала службы:
```
[primo-admin@redos-robot ~]$ sudo journalctl -u Primo.Orchestrator.Agent
```

### Настройка правила брандмауэра Firewall

Установка и настройка брандмауэра Firewall описана в [Руководстве РЕДОС](https://redos.red-soft.ru/base/server-configuring/firewall/configuring-firewall/).

Для разрешения доступа к API агента оркестратора выполните следующее:
```
[primo-admin@redos-robot ~]$ sudo firewall-cmd --zone=public --add-port=5002/tcp --permanent
[primo-admin@redos-robot ~]$ sudo firewall-cmd --reload
```

### Настройка учетной записи робота

Создание учётной записи робота robot1:
```
[primo-admin@redos-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash robot1
```
Установка пароля учётной записи робота robot1:
```
[primo-admin@redos-robot ~]$ sudo passwd robot1
Изменение пароля пользователя robot1.  
Новый пароль: ***  
Повторите ввод нового пароля: ***  
passwd: данные аутентификации успешно обновлены.  
```
После создания учётной записи робота на машине робота войдите в графический сеанс этой учётной записи для инициализации графического окружения.

Рекомендуется отключить фон рабочего стола для экономии памяти. Для этого используйте:  
**ПКМ на рабочем столе -> Параметры внешнего вида -> Фон -> Без фона рабочего стола**

Запомните разрешение экрана, при котором тестируются действия робота - поиск изображений, клики и т.п., чтобы настроить такое же разрешение пользователю робота в Оркестраторе:
**Пуск -> Параметры -> Экраны**

:small_orange_diamond: Рекомендации по настройке пользователя робота в Оркестраторе (пользователя РДП):  
Для экономии памяти используйте минимально необходимую глубину цвета экрана - 24 или 16 бит.

### Обновление агента оркестратора

Остановка службы:
```
[primo-admin@redos-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
```
Обновление файлов агента оркестратора на машине роботов (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@redos-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@redos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
[primo-admin@redos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@redos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent
```
Запуск службы:
```
[primo-admin@redos-robot ~]$ sudo systemctl start Primo.Orchestrator.Agent
```
Просмотр статуса службы:
```
[primo-admin@redos-robot ~]$ sudo systemctl status Primo.Orchestrator.Agent
```

### Миграция агента оркестратора

Для миграции существующей установки агента оркестратора на версию с возможностью работы без прав root выполните следующее:
* настройте пользователей и группы
* перенесите данные агента оркестратора
* обновите агент и файл конфигурации
* обновите файл управления службой

### Настройка пользователей и групп

Эти команды необходимо выполнять от имени пользователя, настроенного как администратор при установке РЕДОС 7.3:
```
[admin@redos-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
[admin@redos-robot ~]$ sudo useradd -m -s /bin/bash primo-admin
[admin@redos-robot ~]$ sudo usermod -G wheel primo-admin
[admin@redos-robot ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```

Теперь небходимо войти в систему под пользователем primo-admin и дальнейшие команды выполнять под его именем.
Выполните команды из следующих разделов:
* Настройка дополнительного ПО
* Настройка учетной записи агента

Существующие учётные записи роботов добавьте в группу primo-rpa:
```
[primo-admin@redos-robot ~]$ sudo usermod -G primo-rpa robot
```

### Перенос данных агента оркестратора

В командах этого раздела предполагаются исходные пути каталогов с данными, совпадающие с оригинальным файлом конфигурации. Если эти пути были изменены, подставьте изменённые пути.
```
[primo-admin@redos-robot ~]$ sudo mkdir /opt/Primo/AgentData 
[primo-admin@redos-robot ~]$ sudo mv /opt/Primo/Agent/RobotLocks /opt/PrimoAgent/RobotDistr /opt/Primo/Agent/ScreenFilesZip /opt/Primo/AgentData
[primo-admin@redos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/AgentData /opt/LTools
[primo-admin@redos-robot ~]$ sudo chmod -R g+w /opt/Primo/AgentData /opt/LTools
```

### Обновление агента и файла конфигурации

Обновление файлов агента оркестратора (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@redos-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@redos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@redos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent 
[primo-admin@redos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
```

В файле конфигурации appsettings.ProdLinux.json внесите следующие изменения:
1.	Вместо:
```
...
"Robot": {
  ...
  "LocksPath": "/opt/Primo/Agent/RobotLocks",
  ...
}
```
укажите:
```
...
"Robot": {
  ...
  "LocksDir": "RobotLocks"
}
```
2.	Вместо:
```
"DeployRobot": {
  ...
  "RobotDistrPath": "/opt/PrimoAgent/RobotDistr",
  ...
}
```
укажите:
```
"DeployRobot": {
  ...
  "RobotDistrDir": "RobotDistr",
  ...
}
```
3.	Вместо:
```
"ScreenFiles": {
  ...
  "ZipPath": "/opt/Primo/Agent/ScreenFilesZip",
  ...
}
```
укажите:
```
"ScreenFiles": {
  ...
  "ZipDir": "ScreenFilesZip",
  ...
}
```
4.	Добавьте:
```
"Agent": {
  ...
  "DataPath": "/opt/Primo/AgentData",
  ...
},
...
"AgentCommands": {
    "At": "/usr/bin/at",
    "Reboot": "/usr/sbin/reboot",
    "Xvfb": "/usr/bin/xvfb-run",
    "Session": "/usr/bin/mate-session"
},
```

### Обновление файла управления службой
```
[primo-admin@redos-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@redos-robot ~]$ sudo systemctl daemon-reload
[primo-admin@redos-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```

## Действия при установке Astra Linux 1.7

При установке машины робота под управлением Astra Linux 1.7 необходимо:

* на экране **Настройка учётных записей и паролей** создать пользователя-администратора (далее - primo-admin)

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-5.PNG)

Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.

### Настройка дополнительного ПО

1. Выполните подключение машины робота к репозиториям main, update, base и extended. 
Сами репозитории описаны в статье [Интернет-репозитории Astra Linux Special Edition x.7](https://wiki.astralinux.ru/pages/viewpage.action?pageId=158598882). 
Настройка локальных зеркал этих репозиториев описана в статье [Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте](https://wiki.astralinux.ru/pages/viewpage.action?pageId=199148426). 

:large_orange_diamond: **Локальные репозитории необходимо выгружать на машине, имеющей доступ в Интернет.**

Рекомендуется выделить одну машину под управлением Astra Linux 1.7 для размещения на ней сервера репозиториев.

Для машины с доступом в Интернет файл `/etc/apt/sources.list` может выглядеть следующим образом:
```
deb https://download.astralinux.ru/astra/stable/1.7_x86-64/repository-main/ 1.7_x86-64 main contrib non-free
deb https://download.astralinux.ru/astra/stable/1.7_x86-64/repository-update/ 1.7_x86-64 main contrib non-free
deb https://download.astralinux.ru/astra/stable/1.7_x86-64/repository-base/ 1.7_x86-64 main contrib non-free
deb https://download.astralinux.ru/astra/stable/1.7_x86-64/repository-extended/ 1.7_x86-64 main contrib non-free
deb https://download.astralinux.ru/astra/stable/1.7_x86-64/repository-extended/ 1.7_x86-64 astra-ce
```

2. Проверьте доступность репозиториев, используя следующую команду:
```
[primo-admin@astra-robot ~]$ sudo apt update
```
Репозитории main, update, base и extended должны присутствовать в выводе команды.

3. Установите необходимое для работы робота ПО:
```
[primo-admin@astra-robot ~]$ sudo apt -y install at xvfb python3-numpy python3-opencv xdotool dotnet-sdk-8.0 graphicsmagick-imagemagick-compat
```

### Настройка учетной записи агента

Для работы агента оркестратора и роботов создайте общую группу:
```
[primo-admin@astra-robot ~]$ sudo groupadd primo-rpa
```
Для работы агента оркестратора создайте учётную запись:
```
[primo-admin@astra-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash agent
```
Если необходимо, задайте пароль учётной записи:
```
[primo-admin@redos-robot ~]$ sudo passwd agent
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```
Для запуска агентом оркестратора заданий роботов без прав пользователя root установите следующую настройку:
```
[primo-admin@astra-robot ~]$ sudo sh -c "echo 'agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-rpa-agent"
[primo-admin@astra-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-rpa-agent"
```

### Режим запуска роботов atd

Для запуска заданий роботов без прав пользователя root файл `/etc/sudoers.d/primo-rpa-agent` должен выглядеть следующим образом:
```
agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot
agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/kill
agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/at
```
Пояснения:
•	первая строка разрешает пользователю agent запуск команды `/usr/sbin/reboot` с правами пользователя root без ввода пароля, то есть, позволяет агенту перезагрузить машину агента;
•	вторая строка разрешает пользователю agent запуск команды `/usr/bin/kill` с правами любого пользователя из группы primo-rpa без ввода пароля, то есть, позволяет агенту завершить процесс любого робота;
•	третья строка разрешает пользователю agent запуск команды `/usr/bin/at` с правами любого пользователя из группы primo-rpa без ввода пароля, то есть, позволяет агенту запустить робота с помощью службы *atd*.


### Режим запуска роботов systemd

Для запуска заданий роботов без прав пользователя root файл `/etc/sudoers.d/primo-rpa-agent` должен выглядеть следующим образом:
```
agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot
agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/kill
agent ALL = (%primo-rpa) NOPASSWD:SETENV: /usr/bin/systemd-run -G --user --unit *
agent ALL = (%primo-rpa) NOPASSWD:SETENV: /usr/bin/systemctl --user stop *
agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/loginctl enable-linger *
```
Пояснения:
•	первая строка разрешает пользователю agent запуск команды `/usr/sbin/reboot` с правами пользователя root без ввода пароля, то есть, позволяет агенту перезагрузить машину агента;
•	вторая строка разрешает пользователю agent запуск команды `/usr/bin/kill` с правами любого пользователя из группы primo-rpa без ввода пароля, то есть, позволяет агенту завершить процесс любого робота;
•	третья строка разрешает пользователю agent запуск команды `/usr/bin/systemd-run` с правами любого пользователя из группы primo-rpa без ввода пароля, то есть, позволяет агенту запустить сеанса робота с помощью службы *systemd*;
•	четвёртая строка разрешает пользователю agent запуск команды `/usr/bin/systemctl` с правами любого пользователя из группы primo-rpa без ввода пароля, то есть, позволяет агенту корректно остановить сеанс робота с помощью службы *systemd*;
•	пятая строка разрешает пользователю agent запуск команды `/usr/bin/loginctl` с правами любого пользователя из группы primo-rpa без ввода пароля, то есть, позволяет агенту включить поддержку сеансов для робота.


### Установка агента

Разворачивание файлов агента оркестратора на машине роботов (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@astra-robot ~]$ sudo mkdir -p /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@astra-robot ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent
[primo-admin@astra-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent /opt/Primo/Agent/LTools.Orchestrator.Agent.Runner
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
```
Установите агент оркестратора как службу и настройте автозапуск:
```
[primo-admin@astra-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@astra-robot ~]$ sudo systemctl daemon-reload
[primo-admin@astra-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```
В конфигурационном файле appsettings.ProdLinux.json укажите адрес Оркестратора и TenantId (если эта машина не в тенанте по умолчанию) и пользователя из тенанта:
```
  "Orchestrator": {
    "UserName": "agent",
    "Password": "<зашифрованный пароль>",
    "BaseUrl": "https://192.168.1.154:44362",
    "DownloadRpaProject": true,
    "UserBaseUrlFromRequest": true,
    "TenantId": ""
  },
  ...
  "Agent": {
    
    ...
    "RobotStartMethod": "system",
  },
```
Убедитесь, что в конфигурационном файле appsettings.ProdLinux.json правильно указаны команды, с помощью которых агент запускает роботов и управляет машиной (здесь указаны правильные команды для Astra Linux 1.7):
```
 "AgentCommands": {
    "At": "/usr/bin/at",
    "Reboot": "/usr/sbin/reboot",
    "Xvfb": "/usr/bin/xvfb-run",
    "Session": "/usr/bin/fly-wm --execOnly {}"
 },
```
Запуск службы:
```
[primo-admin@astra-robot ~]$ sudo systemctl start Primo.Orchestrator.Agent
```
Просмотр статуса службы:
```
[primo-admin@astra-robot ~]$ sudo systemctl status Primo.Orchestrator.Agent
```
Просмотр журнала службы:
```
[primo-admin@astra-robot ~]$ sudo journalctl -u Primo.Orchestrator.Agent
```

### Настройка правила брандмауэра ufw

Установка и настройка брандмауэра ufw описана в статье [Межсетевой экран ufw](https://wiki.astralinux.ru/pages/viewpage.action?pageId=27362474).

Для разрешения доступа к API агента оркестратора выполните следующее:
```
[primo-admin@astra-robot ~]$ sudo ufw allow 5002/tcp
```

### Настройка учетной записи робота

Создание учётной записи робота robot1:
```
[primo-admin@astra-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash robot1
```
Установка пароля учётной записи робота robot1:
```
[primo-admin@astra-robot ~]$ sudo passwd robot1
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```
После создания учётной записи робота на машине робота необходимо войти в графический сеанс этой учётной записи для инициализации графического окружения.
Рекомендуется отключить фон рабочего стола для экономии памяти. Для этого используйте:
**ПКМ на рабочем столе -> Свойства -> Обои, удалить обои и логотип.**

Запомните разрешение экрана, при котором тестируются действия робота - поиск изображений, клики и т.п., чтобы настроить такое же разрешение пользователю робота в Оркестраторе:  
**Пуск -> Настройка монитора**.

:small_orange_diamond: Рекомендации по настройке пользователя робота в Оркестраторе (пользователя РДП):
Для экономии памяти используйте минимально необходимую глубину цвета экрана - 24 или 16 бит.

### Обновление агента оркестратора

Остановка службы:
```
[primo-admin@astra-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
```
Обновление файлов агента оркестратора на машине роботов (файл Agent-linux.zip должен находиться в каталоге `/`srv/samba/shared/install`):
```
[primo-admin@astra-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent 
[primo-admin@astra-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
```
Запуск службы:
```
[primo-admin@astra-robot ~]$ sudo systemctl start Primo.Orchestrator.Agent
```
Просмотр статуса службы:
```
[primo-admin@astra-robot ~]$ sudo systemctl status Primo.Orchestrator.Agent
```

### Миграция агента оркестратора

Для миграции существующей установки агента оркестратора на версию с возможностью работы без прав root выполните следующее:
* настройте пользователей и группы
* перенесите данные агента оркестратора
* обновите агент и файл конфигурации
* обновите файл управления службой

### Настройка пользователей и групп

Эти команды необходимо выполнять от имени пользователя, настроенного как администратор при установке Astra Linux 1.7:
```
[admin@astra-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
[admin@astra-robot ~]$ sudo useradd -m -s /bin/bash primo-admin
[admin@astra-robot ~]$ sudo usermod -G cdrom, floppy, audio, dip, video, plugdev, netdev, lpadmin, astra-console, astra-admin primo-admin
[admin@astra-robot ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```
Теперь войдите в систему под пользователем primo-admin и дальнейшие команды выполняйте под его именем.

Выполните команды из следующих разделов:
* Настройка дополнительного ПО
* Настройка учетной записи агента

Существующие учётные записи роботов добавьте в группу primo-rpa:
```
[primo-admin@astra-robot ~]$ sudo usermod -G primo-rpa robot
```

### Перенос данных агента оркестратора

В командах этого раздела предполагаются исходные пути каталогов с данными, совпадающие с оригинальным файлом конфигурации. Если эти пути были изменены, подставьте изменённые пути.
```
[primo-admin@astra-robot ~]$ sudo mkdir /opt/Primo/AgentData 
[primo-admin@astra-robot ~]$ sudo mv /opt/Primo/Agent/RobotLocks /opt/PrimoAgent/RobotDistr /opt/Primo/Agent/ScreenFilesZip /opt/Primo/AgentData
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
```

### Обновление агента и файла конфигурации

Обновление файлов агента оркестратора (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@astra-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent 
[primo-admin@astra-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
```

В файле конфигурации appsettings.ProdLinux.json внесите следующие изменения:
1.	Вместо:
```
...
"Robot": {
  ...
  "LocksPath": "/opt/Primo/Agent/RobotLocks",
  ...
}
```
укажите:
```
...
"Robot": {
  ...
  "LocksDir": "RobotLocks"
}
```
2.	Вместо:
```
"DeployRobot": {
  ...
  "RobotDistrPath": "/opt/PrimoAgent/RobotDistr",
  ...
}
```
укажите:
```
"DeployRobot": {
  ...
  "RobotDistrDir": "RobotDistr",
  ...
}
```
3.	Вместо:
```
"ScreenFiles": {
  ...
  "ZipPath": "/opt/Primo/Agent/ScreenFilesZip",
  ...
}
```
укажите:
```
"ScreenFiles": {
  ...
  "ZipDir": "ScreenFilesZip",
  ...
}
```
4.	Добавьте:
```
"Agent": {
  ...
  "DataPath": "/opt/Primo/AgentData",
  ...
},
...
AgentCommands": {
    "At": "/usr/bin/at",
    "Reboot": "/usr/sbin/reboot",
    "Xvfb": "/usr/bin/xvfb-run",
    "Session": "/usr/bin/fly-wm --execOnly {}"
},
```

### Обновление файла управления службой

```
[primo-admin@astra-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@astra-robot ~]$ sudo systemctl daemon-reload
[primo-admin@astra-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```

## Действия при установке CentOS 7, 8

При установке машины робота под управлением Centos 7 необходимо:

* на экране **ВЫБОР ПРОГРАММ** отметить базовое окружение **Рабочая станция**:

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-6.PNG)

* на экране **СОЗДАНИЕ ПОЛЬЗОВАТЕЛЕЙ** создать пользователя-администратора (далее - primo-admin):

![](../../../../orchestrator-new/resources/install/linux/setting-up-machines-linux/Agentinstall-7.PNG)

Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.

### Настройка дополнительного ПО

1. Выполните подключение машины робота к репозиториям base, extra и updates. Настройка локальных зеркал этих репозиториев описана в [Create Local Repos](https://wiki.centos.org/HowTos(2f)CreateLocalRepos.html). 

:large_orange_diamond: **Локальные репозитории необходимо выгружать на машине, имеющей доступ в Интернет.**

Рекомендуется выделить одну машину под управлением CentOS 7 для размещения на ней сервера репозиториев.

2. Проверьте доступность репозиториев base, extra и updates, используя следующую команду:
```
[primo-admin@centos-robot ~]$ sudo yum repolist
```
Репозитории base, extra и updates должны присутствовать в выводе команды.

3. Установите необходимое для работы робота ПО:
```
[primo-admin@centos-robot ~]$ sudo yum -y install at xorg-x11-server-Xvfb numpy opencv-python ImageMagick
[primo-admin@centos-robot ~]$ sudo yum -y install epel-release
[primo-admin@centos-robot ~]$ sudo yum -y install xdotool
[primo-admin@centos-robot ~]$ sudo rpm -Uvh https://packages.microsoft.com/config/centos/7/packages-microsoft-prod.rpm
[primo-admin@centos-robot ~]$ sudo yum -y install dotnet-sdk-6.0
```
Для установки пакетов xdotool и dotnet-sdk-6.0 необходимо подключение к сети Internet.

### Настройка учетной записи агента

Для работы агента оркестратора и роботов создайте общую группу:
```
[primo-admin@centos-robot ~]$ sudo groupadd primo-rpa
```
Для работы агента оркестратора создайте учётную запись:
```
[primo-admin@centos-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash agent
```
Если требуется, задайте пароль учётной записи:
```
[primo-admin@centos-robot ~]$ sudo passwd agent
Изменяется пароль пользователя agent.
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: все данные аутентификации успешно обновлены.
```
Для запуска агентом оркестратора заданий роботов без прав пользователя root установите следующую настройку:
```
[primo-admin@centos-robot ~]$ sudo sh -c "echo 'agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-rpa-agent"
[primo-admin@centos-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-rpa-agent"
[primo-admin@centos-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/bin/kill' >> /etc/sudoers.d/primo-rpa-agent"
[primo-admin@centos-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/sysctl' >> /etc/sudoers.d/primo-rpa-agent"
[primo-admin@astra-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /bin/systemctl' >> /etc/sudoers.d/primo-rpa-agent"
```

### Установка агента

Разворачивание файлов агента оркестратора на машине роботов (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@centos-robot ~]$ sudo mkdir -p /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools /opt/Primo/Agent_
[primo-admin@centos-robot ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent
[primo-admin@centos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
[primo-admin@centos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools /opt/Primo/Agent
[primo-admin@centos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools /opt/Primo/Agent
```
Установите агент оркестратора как службу и настройте автозапуск:
```
[primo-admin@centos-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@centos-robot ~]$ sudo systemctl daemon-reload
[primo-admin@centos-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```
Убедитесь, что в конфигурационном файле appsettings.ProdLinux.json правильно указаны команды, с помощью которых агент запускает роботов и управляет машиной (здесь указаны правильные команды для Centos 7):
```
  "AgentCommands": {
    "At": "/usr/bin/at",
    "Reboot": "/usr/sbin/reboot",
    "Xvfb": "/usr/bin/xvfb-run",
    "Session": "/usr/bin/gnome-session"
  },
```
Запуск службы:
```
[primo-admin@centos-robot ~]$ sudo systemctl start Primo.Orchestrator.Agent
```
Просмотр статуса службы:
```
[primo-admin@centos-robot ~]$ sudo systemctl status Primo.Orchestrator.Agent
```
Просмотр журнала службы:
```
[primo-admin@centos-robot ~]$ sudo journalctl -u Primo.Orchestrator.Agent
```

### Настройка правила брандмауэра Firewall

Установка и настройка брандмауэра Firewall описана в [Using Firewalls](https://docs.redhat.com/en/documentation/red_hat_enterprise_linux/7/html/security_guide/sec-using_firewalls).

Для разрешения доступа к API агента оркестратора выполните следующее:
```
[primo-admin@centos-robot ~]$ sudo firewall-cmd --zone=public --add-port=5002/tcp --permanent
[primo-admin@centos-robot ~]$ sudo firewall-cmd --reload
```

### Настройка учетной записи робота

Создание учётной записи робота robot1:
```
[primo-admin@centos-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash robot1
```
Установка пароля учётной записи робота robot1:
```
[primo-admin@centos-robot ~]$ sudo passwd robot1
Изменяется пароль пользователя robot1.
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: все данные аутентификации успешно обновлены.
```

После создания учётной записи робота на машине робота войдите в графический сеанс этой учётной записи для инициализации графического окружения.

Рекомендуется отключить фон рабочего стола для экономии памяти. Для этого используйте:  
**ПКМ на рабочем столе -> Изменить фон**

Запомните разрешение экрана, при котором тестируются действия робота - поиск изображений, клики и т.п., чтобы настроить такое же разрешение пользователю робота в Оркестраторе:  
**Приложения -> Системные -> Параметры -> Устройства -> Дисплеи**

:small_orange_diamond: Рекомендации по настройке пользователя робота в Оркестраторе (пользователя РДП):  
Для экономии памяти используйте минимально необходимую глубину цвета экрана - 24 или 16 бит.

### Обновление агента оркестратора

Остановка службы:
```
[primo-admin@centos-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
```
Обновление файлов агента оркестратора на машине роботов (файл Agent-linux.zip должен находиться в каталоге `/`srv/samba/shared/install`):
```
[primo-admin@centos-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@centos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@centos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent
[primo-admin@centos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
```
Запуск службы:
```
[primo-admin@centos-robot ~]$ sudo systemctl start Primo.Orchestrator.Agent
```
Просмотр статуса службы:
```
[primo-admin@centos-robot ~]$ sudo systemctl status Primo.Orchestrator.Agent
```

### Миграция агента оркестратора

Для миграции существующей установки агента оркестратора на версию с возможностью работы без прав root выполните следующее:
* настройте пользователей и группы
* перенесите данные агента оркестратора
* обновите агент и файл конфигурации
* обновите файл управления службой

### Настройка пользователей и групп

Эти команды необходимо выполнять от имени пользователя, настроенного как администратор при установке CentOS 7:
```
[admin@centos-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
[admin@centos-robot ~]$ sudo useradd -m -s /bin/bash primo-admin
[admin@centos-robot ~]$ sudo usermod -G wheel primo-admin

[admin@centos-robot ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён

```
Теперь небходимо войти в систему под пользователем primo-admin и дальнейшие команды выполнять под его именем.

Выполните команды из следующих разделов:
* Настройка дополнительного ПО
* Настройка учетной записи агента

Существующие учётные записи роботов добавьте в группу primo-rpa:
```
[primo-admin@centos-robot ~]$ sudo usermod -G primo-rpa robot
```

### Перенос данных агента оркестратора

В командах этого раздела предполаются исходные пути каталогов с данными, совпадающие с оригинальным файлом конфигурации. Если эти пути были изменены, то подставьте изменённые пути.
```
[primo-admin@centos-robot ~]$ sudo mkdir /opt/Primo/AgentData 
[primo-admin@centos-robot ~]$ sudo mv /opt/Primo/Agent/RobotLocks /opt/PrimoAgent/RobotDistr /opt/Primo/Agent/ScreenFilesZip /opt/Primo/AgentData
[primo-admin@centos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/AgentData /opt/LTools
[primo-admin@centos-robot ~]$ sudo chmod -R g+w /opt/Primo/AgentData /opt/LTools
```

### Обновление агента и файла конфигурации

Обновление файлов агента оркестратора (файл Agent-linux.zip должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@centos-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@centos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@centos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent 
[primo-admin@centos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
```

В файле конфигурации appsettings.ProdLinux.json внесите следующие изменения:
1. Вместо:
```
...
"Robot": {
  ...
  "LocksPath": "/opt/Primo/Agent/RobotLocks",
  ...
}
```
укажите:
```
...
"Robot": {
  ...
  "LocksDir": "RobotLocks"
}
```
2. Вместо:
```
"DeployRobot": {
  ...
  "RobotDistrPath": "/opt/PrimoAgent/RobotDistr",
  ...
}
```
укажите:
```
"DeployRobot": {
  ...
  "RobotDistrDir": "RobotDistr",
  ...
}
```
3. Вместо:
```
"ScreenFiles": {
  ...
  "ZipPath": "/opt/Primo/Agent/ScreenFilesZip",
  ...
}
```
укажите:
```
"ScreenFiles": {
  ...
  "ZipDir": "ScreenFilesZip",
  ...
}
```
4.	Добавьте:
```
"Agent": {
  ...
  "DataPath": "/opt/Primo/AgentData",
  ...
},
...
"AgentCommands": {
    "At": "/usr/bin/at",
    "Reboot": "/usr/sbin/reboot",
    "Xvfb": "/usr/bin/xvfb-run",
    "Session": "/usr/bin/gnome-session"
},
```

### Обновление файла управления службой

```
[primo-admin@centos-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@centos-robot ~]$ sudo systemctl daemon-reload
[primo-admin@centos-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```

## Проверка настройки машины робота

Проверяем доступность машины Оркестратора с машины робота. На машине робота выполняем команду:
```
curl -k https://<IP-адрес-машины-Оркестратора>:5001/api/version
```
и убеждаемся, что вернется версия Оркестратора.

Проверяем работу Агента на машине робота. На машине Оркестратора выполняем команду:
```
curl -k https://<IP-адрес-машины-Робота>:5002/api/version
```
и убеждаемся, что вернется версия Агента.

