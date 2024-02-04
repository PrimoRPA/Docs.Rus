# Настройка машины робота

## Действия при установке РЕДОС 7.3

При установке машины робота под управлением РЕДОС 7.3 необходимо:
- на экране **ВЫБОР ПРОГРАММ** отметить базовое окружение **Рабочая станция с графическим окружением (MATE)**;

![ВЫБОР ПРОГРАММ](redos-install-software.png)

- на экране **СОЗДАНИЕ ПОЛЬЗОВАТЕЛЕЙ** создать пользователя-администратора (далее - primo-admin).

![СОЗДАНИЕ ПОЛЬЗОВАТЕЛЯ](redos-create-admin.png)

Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.

## Настройка дополнительного ПО

1. Выполните подключение машины робота к репозиториям `base` и `updates`. Настройка локальных зеркал этих репозиториев описана в [Руководстве РЕДОС](https://redos.red-soft.ru/base/server-configuring/service-repositories/create-repo/)

**!!ВАЖНО!! Локальные репозитории необходимо выгружать на машине, имеющей доступ в Интернет.**

Рекомендуется выделить одну машину под управлением РЕДОС 7.3 для размещения на ней сервера репозиториев.

2. Проверьте доступность репозиториев, используя следующую команду:
```
[primo-admin@redos-robot ~]$ sudo dnf repolist
```

Репозитории `base` и `updates` должны присутствовать в выводе команды.

3. Удалите приложения для автообновления ПО (чтобы избежать засорения рабочего стола робота оповещениями):
```
[primo-admin@redos-robot ~]$ sudo dnf -y remove dnfdragora
```

4. Установите необходимое для работы робота ПО:
```
[primo-admin@redos-robot ~]$ sudo dnf -y install at xorg-x11-server-Xvfb python3-numpy python3-opencv xdotool dotnet-sdk-6.0 ImageMagick
```

## Настройка учетной записи агента

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

Для запуска агентом оркестратора заданий роботов без прав пользователя `root` установите следующую настройку:
```
[primo-admin@redos-robot ~]$ sudo sh -c "echo 'agent ALL = (%primo-rpa) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-rpa-agent"
[primo-admin@redos-robot ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-rpa-agent"
```

## Установка агента

Разворачивание файлов агента оркестратора на машине роботов (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@redos-robot ~]$ sudo mkdir -p /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@redos-robot ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent
[primo-admin@redos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
[primo-admin@redos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
[primo-admin@redos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent /opt/Primo/AgentData /opt/LTools
```

Установите агент оркестратора как службу и настройте автозапуск:
```
[primo-admin@redos-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@redos-robot ~]$ sudo systemctl daemon-reload
[primo-admin@redos-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
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

Убедитесь, что в конфигурационном файле `appsettings.ProdLinux.json` правильно указаны команды, с помощью которых агент запускает роботов и управляет машиной (здесь указаны правильные команды для РЕДОС 7.3):
<pre>
  "AgentCommands": {
    <b>"At": "/usr/bin/at",</b>
    <b>"Reboot": "/usr/sbin/reboot",</b>
    <b>"Xvfb": "/usr/bin/xvfb-run",</b>
    <b>"Session": "/usr/bin/mate-session"</b>
  },
</pre>

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

## Настройка правила брандмауэра Firewall

Установка и настройка брандмауэра Firewall описана в [Руководстве РЕДОС](https://redos.red-soft.ru/base/server-configuring/firewall/configuring-firewall/).

Для разрешения доступа к API агента оркестратора выполните следующее:
```
[primo-admin@redos-robot ~]$ sudo firewall-cmd --zone=public --add-port=5002/tcp --permanent
[primo-admin@redos-robot ~]$ sudo firewall-cmd --reload
```

## Настройка учетной записи робота

Создание учётной записи робота `robot1`:
```
[primo-admin@redos-robot ~]$ sudo useradd -g primo-rpa -m -s /bin/bash robot1
```

Установка пароля учётной записи робота `robot1`:
```
[primo-admin@redos-robot ~]$ sudo passwd robot1
Изменение пароля пользователя robot1.
Новый пароль: ***
Повторите ввод нового пароля: ***
passwd: данные аутентификации успешно обновлены.
```

После создания учётной записи робота на машине робота войдите в графический сеанс этой учётной записи для инициализации графического окружения.

Рекомендуется отключить фон рабочего стола для экономии памяти. Для этого используйте: 

*ПКМ на рабочем столе -> Параметры внешнего вида -> Фон -> Без фона рабочего стола*

Запомните разрешение экрана, при котором тестируются действия робота - поиск изображений, клики и т.п., чтобы настроить такое же разрешение пользователю робота в Оркестраторе:

*Пуск -> Параметры -> Экраны*

**Рекомендации по настройке пользователя робота в Оркестраторе (пользователя РДП):**  
Для экономии памяти используйте минимально необходимую глубину цвета экрана - 24 или 16 бит.

## Обновление агента оркестратора

Остановка службы:
```
[primo-admin@redos-robot ~]$ sudo systemctl stop Primo.Orchestrator.Agent
```

Обновление файлов агента оркестратора на машине роботов (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
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

## Миграция агента оркестратора

Для миграции существующей установки агента оркестратора на версию с возможностью работы без прав `root` выполните следующее:
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

Теперь небходимо войти в систему под пользователем `primo-admin` и дальнейшие команды выполнять под его именем.

Выполните команды из следующих разделов:
* [Настройка дополнительного ПО](#Настройка-дополнительного-ПО)
* [Настройка учетной записи агента](#Настройка-учетной-записи-агента)

Существующие учётные записи роботов добавьте в группу `primo-rpa`: 
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

Обновление файлов агента оркестратора (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@redos-robot ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@redos-robot ~]$ sudo chown -R agent.primo-rpa /opt/Primo/Agent
[primo-admin@redos-robot ~]$ sudo chmod -R g+w /opt/Primo/Agent 
[primo-admin@redos-robot ~]$ sudo chmod a+x /opt/Primo/Agent/Primo.Orchestrator.Agent
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
    "Session": "/usr/bin/mate-session"
},
```

### Обновление файла управления службой

```
[primo-admin@redos-robot ~]$ sudo cp /opt/Primo/Agent/Primo.Orchestrator.Agent.service /etc/systemd/system/
[primo-admin@redos-robot ~]$ sudo systemctl daemon-reload
[primo-admin@redos-robot ~]$ sudo systemctl enable /etc/systemd/system/Primo.Orchestrator.Agent.service
```

