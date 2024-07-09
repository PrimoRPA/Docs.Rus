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
 

## 1. Действия при установке Astra Linux

При установке Astra Linux на целевой машине необходимо создать пользователя-администратора. Для этого на экране «Настройка учетных записей и паролей» введите имя `primo-admin` для учетной записи администратора.

![Настройка учетных записей и паролей](<../../../.gitbook/assets1/primo-ai/install/create-admin-user.png>)

Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.

### Настройка дополнительного ПО

Выполните подключение машины робота к репозиториям `main`, `update`, `base` и `extended`. Сами репозитории описаны в статье [Интернет-репозитории Astra Linux Special Edition x.7](https://wiki.astralinux.ru/pages/viewpage.action?pageId=158598882). Настройка локальных зеркал этих репозиториев описана в статье [Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте](https://wiki.astralinux.ru/pages/viewpage.action?pageId=199148426).

:large_orange_diamond:***Важно**. Локальные репозитории необходимо выгружать на машине, имеющей доступ в интернет.*

Рекомендуется выделить одну машину под управлением Astra Linux для размещения на ней сервера репозиториев.

Проверьте доступность репозиториев, используя следующую команду: 
```
[primo-admin@astra-machine ~]$ sudo apt update
```
Репозитории `main`, `update`, `base` и `extended` должны присутствовать в выводе команды.

### Настройка учетной записи агента

Для работы агента и IDP создайте общую группу:
```
[primo-admin@astra-machine ~]$ sudo groupadd primo-ai
```
Для работы агента создайте учетную запись:
```
[primo-admin@astra-machine ~]$ sudo useradd -g primo-ai -m -s /bin/bash agent
```
Задайте пароль учетной записи:
```
[primo-admin@redos-robot ~]$ sudo passwd agent
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлен
```


### Установка агента

Разворачивание файлов агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@astra-machine ~]$ sudo mkdir -p /opt/Primo.AI/Agent /opt/Primo.AI/AgentData 
[primo-admin@astra-machine ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent /opt/Primo.AI/AgentData /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent /opt/Primo.AI/AgentData /opt/Primo.AI/Agent
```

Установите агент как службу и настройте автозапуск:
```
[primo-admin@astra-machine ~]$ sudo cp /opt/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
[primo-admin@astra-machine ~]$ sudo systemctl daemon-reload
[primo-admin@astra-machine ~]$ sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```

В конфигурационном файле `appsettings.ProdLinux.json` укажите адрес Primo.AI.Api и его компонентов, TenantId (если эта машина не в тенанте по умолчанию) и пользователя тенанта:
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

Убедитесь, что в конфигурационном файле `appsettings.ProdLinux.json` правильно указан путь к стандартным скриптам, с помощью которых агент запускает процессы IDP:
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

Для разрешения доступа к API агента выполните команду:
```
[primo-admin@astra-machine ~]$ sudo ufw allow 5002/tcp
```

### Настройка учетной записи IDP
Создание учетной записи IDP `idp`:
```
[primo-admin@astra-machine ~]$ sudo useradd -g primo-ai -m -s /bin/bash idp
```
Для запуска агентом заданий роботов без прав пользователя `root` установите следующую настройку:
```
[primo-admin@astra-machine ~]$ sudo sh -c "echo idp ALL = (%primo-ai) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/idp"
[primo-admin@astra-machine ~]$ sudo sh -c "echo idp ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/idp"
```

### Обновление агента
Остановка службы:
```
[primo-admin@astra-machine ~]$ sudo systemctl stop Primo.AI.Agent
```
Обновление файлов агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
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
Эти команды необходимо выполнять от имени пользователя, настроенного в качестве администратора при установке Astra Linux:

```
[admin@astra-machine ~]$ sudo systemctl stop Primo.AI.Agent

[admin@astra-machine ~]$ sudo useradd -m -s /bin/bash primo-admin

[admin@astra-machine ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
```

Теперь войдите в систему под пользователем `primo-admin` и дальнейшие команды выполняйте под его именем.

Существующие учетные записи IDP добавьте в группу **primo-ai**:
```
[primo-admin@astra-machine ~]$ sudo usermod -G primo-ai robot
```

### Обновление агента и файла конфигурации
Обновление файлов агента (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
[primo-admin@astra-machine ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent 
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent
```

### Обновление файла управления службой

Выполните команды:
```
[primo-admin@astra-machine ~]$ sudo cp /opt/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
[primo-admin@astra-machine ~]$ sudo systemctl daemon-reload
[primo-admin@astra-machine ~]$ sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```

## 2. Настройка IDP-ядра

Установите библиотеку python3, tesseract и другие пакеты с помощью команд:
```
# apt-get update 
# apt install python3=3.11 python3-venv=3.11 libsm6 libxext6 tesseract-ocr 
```

Создайте папку с инсталляцией:
```
# mkdir /opt/Primo.AI/IDP
```

Скопируйте папку `/srv/samba/shared/install/IDP` в каталог `/opt/Primo.AI/IDP`:
```
# cp -R /srv/samba/shared/install/IDP/* /opt/Primo.AI/IDP
```

Установите права запуска для пользователя `idp`:
```
# chown idp /opt/Primo.AI/IDP/*
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/IDP
[primo-admin@astra-machine ~]$ sudo chown -R idp.primo-ai /opt/Primo.AI/IDP 
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/IDP
```

Создание и активация виртуальной среды venv:
```
# python3 –m venv /opt/Primo.AI/IDP/venv
# source /opt/Primo.AI/IDP/venv/bin/activate
```

Установка пакетов python. 
```
# python -m ensurepip –upgrade
```
•	Если для IDP-процесса будет использоваться CPU:
```
# pip3 install –r /opt/Primo.AI/IDP/prequisites_cpu.txt
# pip3 install –r /opt/Primo.AI/IDP/requirements_cpu.txt
```
•	Если для IDP-процесса будет использоваться GPU:

```
# pip3 install –r /opt/Primo.AI/IDP/prequisites.txt	
# pip3 install –r /opt/Primo.AI/IDP/requirements.txt
```

## 3. Проверка настройки целевой машины

Проверьте доступность Primo.AI.Api с целевой машины. На целевой машине выполните команду:
```
# curl -k https://<IP-адрес-Primo.Ai.Api>:44392/api/version
```

Убедитесь, что вернулась версия Primo.Ai.Api.

Проверьте работу агента на целевой машине. На машине Primo.Ai.Api выполните команду:
```
# curl -k https://<IP-адрес-целевой-машины>:5002/api/version
```
Убедитесь,, что вернулась версия агента.


