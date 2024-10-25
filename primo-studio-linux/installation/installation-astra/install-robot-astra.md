# Настройка машины робота


## Действия при установке Astra Linux 1.7


При установке машины робота под управлением Astra Linux 1.7 необходимо:
- на экране **Настройка учетных записей и паролей** создать пользователя-администратора (далее — `primo-admin`).


![СОЗДАНИЕ ПОЛЬЗОВАТЕЛЯ](../../../.gitbook/assets1/astra-create-admin1.png)


Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.


## Настройка дополнительного ПО


1. Выполните подключение машины робота к репозиториям `main`, `update`, `base` и `extended`. Сами репозитории описаны в статье [Интернет-репозитории Astra Linux Special Edition x.7](https://wiki.astralinux.ru/pages/viewpage.action?pageId=158598882). Настройка локальных зеркал этих репозиториев описана в статье [Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте](https://wiki.astralinux.ru/pages/viewpage.action?pageId=199148426).

   Рекомендуется выделить одну машину под управлением Astra Linux 1.7 для размещения на ней сервера репозиториев.

{% hint style="warning" %}
**Важно**. Локальные репозитории необходимо выгружать на машине, имеющей доступ в интернет.
{% endhint %}


2. Проверьте доступность репозиториев, используя следующую команду:

   ```
   [primo-admin@astra-robot ~]$ sudo apt update
   ```

   Репозитории `main`, `update`, `base` и `extended` должны присутствовать в выводе команды.


3. Установите необходимое для работы робота ПО:
   ```
   [primo-admin@astra-robot ~]$ sudo apt -y install xsel at xvfb python3 python3-pyatspi python3-numpy xdotool imagemagick python3-opencv wmctrl
   ```


## Настройка учетной записи агента

Для работы агента Оркестратора и роботов создайте общую группу:
```
[primo-admin@astra-robot ~]$ sudo groupadd primo-rpa
```

Для работы агента Оркестратора создайте учетную запись:
```
[primo-admin@astra-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash agent
```


Если необходимо, задайте пароль учетной записи:

```
[primo-admin@redos-robot ~]$ sudo passwd agent
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлен
```

Для запуска агентом Оркестратора заданий роботов без прав пользователя `root` установите следующую настройку:
```
[primo-admin@astra-robot ~]$ sudo sh -c "echo 'agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-rpa-agent"
[primo-admin@astra-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-rpa-agent"
```



## Установка агента

Разворачивание файлов агента Оркестратора на машине роботов (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@astra-robot ~]$ sudo mkdir -p /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@astra-robot ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent
[primo-admin@astra-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
```

Установите агент Оркестратора как службу и настройте автозапуск:
```
[primo-admin@astra-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@astra-robot ~]$ sudo systemctl daemon-reload
[primo-admin@astra-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```


В конфигурационном файле `appsettings.ProdLinux.json` укажите адрес Оркестратора и TenantId (если эта машина не в тенанте по умолчанию) и пользователя из тенанта, а также адрес машины робота:
<pre>
  "Orchestrator": {
    "UserName": "agent",
    "Password": "Qwe123!@#",
    <b>"BaseUrl": "https://192.168.1.154:5001",</b>
    "DownloadRpaProject": true,
    "UserBaseUrlFromRequest": true,
    "TenantId": ""
  },
  ...
  "Agent": {
    ...
    <b>"IpAddress": "192.168.0.20",</b>
    ...
  },
</pre>


Убедитесь, что в конфигурационном файле `appsettings.ProdLinux.json` правильно указаны команды, с помощью которых агент запускает роботов и управляет машиной (здесь указаны правильные команды для Astra Linux 1.7):
<pre>
  "AgentCommands": {
    <b>"At": "/usr/bin/at",</b>
    <b>"Reboot": "/usr/sbin/reboot",</b>
    <b>"Xvfb": "/usr/bin/xvfb-run",</b>
    <b>"Session": "/usr/bin/fly-wm"</b>
  },
</pre>


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


## Настройка правила брандмауэра `ufw`

Установка и настройка брандмауэра `ufw` описана в статье [Межсетевой экран ufw](https://wiki.astralinux.ru/pages/viewpage.action?pageId=27362474).

Для разрешения доступа к API агента Оркестратора выполните следующее:
```
[primo-admin@astra-robot ~]$ sudo ufw allow 5002/tcp
```


## Настройка учетной записи робота

Создание учётной записи робота `robot1`:
```
[primo-admin@astra-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash robot1
```


Установка пароля учетной записи робота `robot1`:
```
[primo-admin@astra-robot ~]$ sudo passwd robot1
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлен
```


После создания учетной записи робота на машине робота необходимо войти в графический сеанс этой учётной записи для инициализации графического окружения.

Рекомендуется отключить фон рабочего стола для экономии памяти. Для этого используйте: 


*ПКМ на рабочем столе -> Свойства -> Обои, удалить обои и логотип.*


Запомните разрешение экрана, при котором тестируются действия робота - поиск изображений, клики и т.п., чтобы настроить такое же разрешение пользователю робота в Оркестраторе:

*Пуск -> Настройка монитора.*


**Рекомендации по настройке пользователя робота в Оркестраторе (пользователя РДП):**  
Для экономии памяти используйте минимально необходимую глубину цвета экрана — 24 или 16 бит.


## Обновление агента Оркестратора

Остановка службы:
```
[primo-admin@astra-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
```


Обновление файлов агента Оркестратора на машине роботов (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
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


## Миграция агента Оркестратора


Для миграции существующей установки агента Оркестратора на версию с возможностью работы без прав `root` выполните следующее:
* настройте пользователей и группы;
* перенесите данные агента Оркестратора;
* обновите агент и файл конфигурации;
* обновите файл управления службой.


### Настройка пользователей и групп


Эти команды необходимо выполнять от имени пользователя настроенного как администратор при установке Astra Linux 1.7:
```
[admin@astra-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
[admin@astra-robot ~]$ sudo useradd -m -s /bin/bash primo-admin
[admin@astra-robot ~]$ sudo usermod -G cdrom,floppy,audio,dip,video,plugdev,netdev,lpadmin,astra-console,astra-admin primo-admin
[admin@astra-robot ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```


Теперь войдите в систему под пользователем `primo-admin` и дальнейшие команды выполняйте под его именем.


Выполните команды из следующих разделов:
* [Настройка дополнительного ПО](#Настройка-дополнительного-ПО)
* [Настройка учетной записи агента](#Настройка-учетной-записи-агента)


Существующие учетные записи роботов добавьте в группу `primo-rpa`: 
```
[primo-admin@astra-robot ~]$ sudo usermod -G primo-rpa robot
```


### Перенос данных агента Оркестратора


В командах этого раздела предполагаются исходные пути каталогов с данными, совпадающие с оригинальным файлом конфигурации. Если эти пути были изменены, подставьте измененные пути.

```
[primo-admin@astra-robot ~]$ sudo mkdir /opt/Primo/AgentData 
[primo-admin@astra-robot ~]$ sudo mv /opt/Primo/Agent/RobotLocks /opt/PrimoAgent/RobotDistr /opt/Primo/Agent/ScreenFilesZip /opt/Primo/AgentData
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
```


### Обновление агента и файла конфигурации


Обновление файлов агента Оркестратора (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@astra-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@astra-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent 
[primo-admin@astra-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
```


В файле конфигурации `appsettings.ProdLinux.json` внесите следующие изменения:
1) Вместо:
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
2) Вместо:
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
3) Вместо:
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
4) Добавьте:
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
    "Session": "/usr/bin/fly-wm",
    "StopSession": "fly-wmfunc FLYWM_UPDATE_VAL UseExitDialog false && fly-wmfunc FLYWM_UPDATE_VAL UseConfirmDialog false && fly-wmfunc FLYWM_LOGOUT"
},
```


### Обновление файла управления службой

```
[primo-admin@astra-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@astra-robot ~]$ sudo systemctl daemon-reload
[primo-admin@astra-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```
