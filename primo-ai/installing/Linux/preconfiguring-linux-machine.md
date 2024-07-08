# Настройка целевой машины для Linux

## Предполагаемая аудитория 

Раздел предназначен для системных администраторов, имеющих следующие навыки и знания:
1. Обязательно – уверенный пользователь ОС Linux:
   *	Владеть основными командами для перемещения в папках и файлах.
   *	Уметь создавать и редактировать текстовые файлы.
   *	Уметь копировать файлы, текст из файлов, сохранять файлы.
1. Обязательно – опыт администрирования ОС Linux:
   * Уметь запускать программы и скрипты.
   * Иметь опыт работы c bash.
   * Иметь опыт сетевого и системного администрирования ОС Linux.

## Системные требования
 
Для целевой машины следует использовать рабочую станцию под управлением Linux, к которой предъявляются требования из таблицы ниже.

| Параметр        | Требование                     | Примечание   |
| --------------- | ------------------------------ | ------------ |
| CPU             | 4 ядра	                        |  |
| RAM             | 8 Гб	                          |  |
| HDD             | 250 Гб (OS + Data)	            |  |

## Файлы из комплекта поставки

На целевую машину необходимо скопировать файлы из комплекта поставки Primo RPA AI Server, приведенные в таблице ниже. Остальное ПО должно быть предустановлено в Linux.

| Файл            | Описание                              | Примечание   |
| --------------- | ------------------------------------- | ------------ |
| Agent-linux.zip | Дистрибутив агента	                  |  |
| IDP.zip         | Дистрибутив IDP	                      |  |


## Введение

Компоненты Primo.AI.Api (выборочно) и их связи и с целевыми машинами приведены на схеме:

![Компоненты Primo.AI.Api и целевые машины](<../../../.gitbook/assets1/primo-ai/install/components-and-machines-scheme.png>)

**Агент** – self-hosted веб-приложение, REST API. Агент выполнен как NET8-приложение. Агент устанавливается на целевой машине и используется для управления IDP.

**IDP** – data science-ядро с нейронными сетями и OCR. Предназначено для интеллектуальной обработки документов. Размещено на специальным образом настроенной целевой машине.

На одной целевой машине может работать только один агент – это ограничение обусловлено полной нагрузкой машины IDP-процессом. Целевых машин может быть много. Все целевые машины должны быть настроены одинаково, и на каждой целевой машине должен быть развернут агент. Версии ОС на целевых машинах могут отличаться

Порт `44392`, указанный на схеме выше, используется при настройке конфигурационных файлов агента и открытия портов на файерволе (в том числе аппаратном в сети организации). Для настройки целевой машины нужна чистая  машина с ОС Linux (обязательно с последними обновлениями). На машину необходимо скопировать папку с комплектом поставки (см. ниже «Комплект поставки»). Это может быть любая папка, но для определенности пусть будет папка `/srv/samba/shared/install`.

Для настройки целевой машины требуется последовательно выполнить все шаги настоящего руководства.
 

## Действия при установке Astra Linux

При установке Astra Linux на целевой машине необходимо создать пользователя-администратора. Для этого на экране «Настройка учетных записей и паролей» введите имя `primo-admin` для учетной записи администратора.

![Настройка учетных записей и паролей](<../../../.gitbook/assets1/primo-ai/install/create-admin-user.png>)

Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.

### Настройка дополнительного ПО

1. Выполните подключение машины робота к репозиториям main, update, base и extended. Сами репозитории описаны в статье Интернет-репозитории Astra Linux Special Edition x.7 . Настройка локальных зеркал этих репозиториев описана в статье Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте 

   !!ВАЖНО!! Локальные репозитории необходимо выгружать на машине, имеющей доступ в Интернет.

   Рекомендуется выделить одну машину под управлением Astra Linux для размещения на ней сервера репозиториев.

   Проверьте доступность репозиториев, используя следующую команду: 
   ```
   [primo-admin@astra-machine ~]$ sudo apt update
   ```
   Репозитории main, update, base и extended должны присутствовать в выводе команды.

1. Установите необходимое для работы робота ПО:
   ```
   [primo-admin@astra-machine ~]$ sudo apt -y install at xvfb python3-numpy python3-opencv xdotool dotnet-sdk-6.0 graphicsmagick-imagemagick-compat
   ```

### Настройка учетной записи агента

Для работы агента и IDP создайте общую группу:
```
[primo-admin@astra-machine ~]$ sudo groupadd primo-ai
```
Для работы агента создайте учётную запись:
```
[primo-admin@astra-machine ~]$ sudo useradd -g primo-ai -m -s /bin/bash agent
```
Если необходимо, задайте пароль учетной записи:
```
[primo-admin@redos-robot ~]$ sudo passwd agent
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```

Для запуска агентом заданий роботов без прав пользователя root установите следующую настройку:
```
[primo-admin@astra-machine ~]$ sudo sh -c "echo 'agent ALL = (%primo-ai) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-ai-agent"
[primo-admin@astra-machine ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-ai-agent"
```

### Установка агента

Разворачивание файлов агента на целевой машине (файл Agent-linux.zip должен находиться в каталоге /srv/samba/shared/install):
```
[primo-admin@astra-machine ~]$ sudo mkdir -p /opt/Primo.AI/Agent /opt/Primo.AI/AgentData 
[primo-admin@astra-machine ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent /opt/Primo.AI/AgentData /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent /opt/Primo.AI/AgentData /opt/Primo.AI/Agent
Установите агент как службу и настройте автозапуск:
[primo-admin@astra-machine ~]$ sudo cp /opt/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
[primo-admin@astra-machine ~]$ sudo systemctl daemon-reload
[primo-admin@astra-machine ~]$ sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```

В конфигурационном файле appsettings.ProdLinux.json укажите адрес Primo.AI.Api, его компонентов и TenantId (если эта машина не в тенанте по умолчанию) и пользователя из тенанта:
```
 	"Api": {
    		"UserName": "agent",
    		"Password": "Qwe123!@#",

    		"AuthBaseUrl": "https://primo-ai-api-server:44392",
    		"ApiBaseUrl": "https://primo-ai-api-server:44392",
    		"InferenceBaseUrl": "https://primo-ai-api-server:44392",
    		"LogsBaseUrl": "https://primo-ai-api-server:44392",

    		"TenantId": ""
  },
```

Убедитесь, что в конфигурационном файле appsettings.ProdLinux.json правильно указан путь к стандартным скриптам, с помощью которых агент запускает процессы IDP:
```
"TrainProcess": {
  "ProcessFileName": "/opt/Primo.AI/IDP/start_training.sh"
},
"InferenceProcess": {
  "ProcessFileName": "/opt/Primo.AI/IDP/start_inference.sh"
},
"TestProcess": {
  "ProcessFileName": "/opt/Primo.AI/IDP/start_evaluation.sh"
},
```

Запуск службы:
```
[primo-admin@astra-machine ~]$ sudo systemctl start Primo.AI.Agent
```

Просмотр статуса службы:
```
[primo-admin@astra-machine ~]$ sudo systemctl status Primo.AI.Agent
```

Просмотр журнала службы:
```
[primo-admin@astra-machine ~]$ sudo journalctl -u Primo.AI.Agent
```

### Настройка правила брандмауэра ufw

Установка и настройка брандмауэра ufw описана в статье Межсетевой экран ufw.
Для разрешения доступа к API агента выполните следующее:
```
[primo-admin@astra-machine ~]$ sudo ufw allow 5002/tcp
```

### Настройка учетной записи IDP
Создание учётной записи IDP idp:
```
[primo-admin@astra-machine ~]$ sudo useradd -g primo-ai -m -s /bin/bash idp
```
Установка пароля учётной записи IDP idp:
```
[primo-admin@astra-machine ~]$ sudo passwd idp
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```

### Обновление агента
Остановка службы:
```
[primo-admin@astra-machine ~]$ sudo systemctl stop Primo.AI.Agent
```
Обновление файлов агента на Целевой машине (файл Agent-linux.zip должен находиться в каталоге /srv/samba/shared/install):
```
[primo-admin@astra-machine ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent 
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent
```
Запуск службы:
```
[primo-admin@astra-machine ~]$ sudo systemctl start Primo.AI.Agent
```
Просмотр статуса службы:
```
[primo-admin@astra-machine ~]$ sudo systemctl status Primo.AI.Agent
```

### Настройка пользователей и групп
Эти команды необходимо выполнять от имени пользователя, настроенного как администратор при установке Astra Linux:
```
[admin@astra-machine ~]$ sudo systemctl stop Primo.AI.Agent
[admin@astra-machine ~]$ sudo useradd -m -s /bin/bash primo-admin
[admin@astra-machine ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```
Теперь войдите в систему под пользователем primo-admin и дальнейшие команды выполняйте под его именем.
Выполните команды из следующих разделов:
•	Настройка дополнительного ПО
•	Настройка учетной записи агента
Существующие учётные записи IDP добавьте в группу primo-ai:
```
[primo-admin@astra-machine ~]$ sudo usermod -G primo-ai robot
```

### Обновление агента и файла конфигурации
Обновление файлов агента (файл Agent-linux.zip должен находиться в каталоге /srv/samba/shared/install):
```
[primo-admin@astra-machine ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent 
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent
```

### Обновление файла управления службой
```
[primo-admin@astra-machine ~]$ sudo cp /opt/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
[primo-admin@astra-machine ~]$ sudo systemctl daemon-reload
[primo-admin@astra-machine ~]$ sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```
