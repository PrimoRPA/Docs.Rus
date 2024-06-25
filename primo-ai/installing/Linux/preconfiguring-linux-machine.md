# Настройка целевой машины для Linux

## Введение

Компоненты Primo.AI.Api (выборочно ) и их связи и с Целевыми машинами приведены на схеме (рисунок 1):

Агент – self-hosted веб-приложение, REST API. Агент выполнен как NET8-приложение. Агент используется для управления IDP на Целевой машине.
IDP – data science-ядро с нейронными сетями и OCR. Предназначено для интеллектуальной обработки документов. Размещено на специальным образом настроенной Целевой машине.
На одной Целевой машине может работать только один агент – это ограничение обусловлено полной нагрузкой машины IDP-процессом. Все Целевые машины должны быть настроены одинаково (версии ОС могут отличаться), и на каждой Целевой машине должен быть развернут Агент.
Целевых машин может быть много.
Порт 44392, указанные выше (рисунок 1), далее используются при настройке конфигурационных файлов Агента и открытия портов на файерволе (в том числе аппаратном в сети организации).
Для настройки Целевой машины нужна (желательно ) чистая  машина с 
Linux (обязательно с последними обновлениями). И на неё должна быть скопирована папка с комплектом поставки (см. ниже «Комплект поставки»). Это может быть любая папка, для определенности, пусть будет папка /srv/samba/shared/install .
Для настройки Целевой машины требуется выполнить шаги настоящего руководства.
 
Требования к персоналу
Документ предназначен для системных администраторов, имеющих навыки:
1.	Обязательно – уверенный пользователь ОС Linux:
a.	Владеть основными командами для перемещения по папкам и файлам.
b.	Создавать и редактировать текстовые файлы.
c.	Копировать файлы, копировать текст из файлов, сохранять файлы. 
2.	Обязательно – опыт администрирования ОС Linux:
a.	Уметь запускать программы и скрипты.
b.	Иметь опыт работы c bash.
c.	Иметь опыт сетевого и системного администрирования ОС Linux.
 
Файлы из комплекта поставки Primo.AI.
Для настройки машины робота потребуются следующие файлы из комплекта поставки Primo.AI (таблица 1):
Таблица 1 – Файлы из комплекта поставки Primo.AI, требуемые для настройки Целевой машины
№
п/п	Наименование файла	Описание	Примечание
1.	Agent-linux.zip	Дистрибутив Агента	
2.	IDP.zip	Дистрибутив IDP	

Остальное ПО должно быть предустановлено в Linux.
 
Аппаратные требования
Для Целевой машины требуется рабочая станция под управлением Linux (таблица 2):
Таблица 2 – Аппаратные требования
№
п/п	Параметр	Требование
1.		CPU	4 ядра
2.		RAM	8 Гб
3.		HDD	250 Гб (OS + Data)
 
1.	Действия при установке Astra Linux
При установке Целевой машины под управлением Astra Linux необходимо:
•	на экране Настройка учётных записей и паролей создать пользователя-администратора (далее - primo-admin).
 
Установка дополнительного ПО и создание дополнительных пользователей будет описана ниже.
Настройка дополнительного ПО
1.	Выполните подключение машины робота к репозиториям main, update, base и extended. Сами репозитории описаны в статье Интернет-репозитории Astra Linux Special Edition x.7 . Настройка локальных зеркал этих репозиториев описана в статье Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте 
!!ВАЖНО!! Локальные репозитории необходимо выгружать на машине, имеющей доступ в Интернет.
Рекомендуется выделить одну машину под управлением Astra Linux для размещения на ней сервера репозиториев.
Проверьте доступность репозиториев, используя следующую команду: 
[primo-admin@astra-machine ~]$ sudo apt update
Репозитории main, update, base и extended должны присутствовать в выводе команды.
3.	Установите необходимое для работы робота ПО:
[primo-admin@astra-machine ~]$ sudo apt -y install at xvfb python3-numpy python3-opencv xdotool dotnet-sdk-6.0 graphicsmagick-imagemagick-compat
Настройка учетной записи агента
Для работы агента и IDP создайте общую группу:
[primo-admin@astra-machine ~]$ sudo groupadd primo-ai
Для работы агента создайте учётную запись:
[primo-admin@astra-machine ~]$ sudo useradd -g primo-ai -m -s /bin/bash agent
Если необходимо, задайте пароль учётной записи:
[primo-admin@redos-robot ~]$ sudo passwd agent
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён

Для запуска агентом заданий роботов без прав пользователя root установите следующую настройку:
[primo-admin@astra-machine ~]$ sudo sh -c "echo 'agent ALL = (%primo-ai) NOPASSWD: /usr/bin/at' > /etc/sudoers.d/primo-ai-agent"
[primo-admin@astra-machine ~]$ sudo sh -c "echo 'agent ALL = (ALL) NOPASSWD: /usr/sbin/reboot' >> /etc/sudoers.d/primo-ai-agent"
Установка агента
Разворачивание файлов агента на Целевой машине (файл Agent-linux.zip должен находиться в каталоге /srv/samba/shared/install):
[primo-admin@astra-machine ~]$ sudo mkdir -p /opt/Primo.AI/Agent /opt/Primo.AI/AgentData 
[primo-admin@astra-machine ~]$ sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent /opt/Primo.AI/AgentData /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent /opt/Primo.AI/AgentData /opt/Primo.AI/Agent
Установите агент как службу и настройте автозапуск:
[primo-admin@astra-machine ~]$ sudo cp /opt/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
[primo-admin@astra-machine ~]$ sudo systemctl daemon-reload
[primo-admin@astra-machine ~]$ sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
В конфигурационном файле appsettings.ProdLinux.json укажите адрес Primo.AI.Api, его компонентов и TenantId (если эта машина не в тенанте по умолчанию) и пользователя из тенанта:
 	"Api": {
    		"UserName": "agent",
    		"Password": "Qwe123!@#",

    		"AuthBaseUrl": "https://primo-ai-api-server:44392",
    		"ApiBaseUrl": "https://primo-ai-api-server:44392",
    		"InferenceBaseUrl": "https://primo-ai-api-server:44392",
    		"LogsBaseUrl": "https://primo-ai-api-server:44392",

    		"TenantId": ""
  },
Убедитесь, что в конфигурационном файле appsettings.ProdLinux.json правильно указан путь к стандартным скриптам, с помощью которых агент запускает процессы IDP:
"TrainProcess": {
  "ProcessFileName": "/opt/Primo.AI/IDP/start_training.sh"
},
"InferenceProcess": {
  "ProcessFileName": "/opt/Primo.AI/IDP/start_inference.sh"
},
"TestProcess": {
  "ProcessFileName": "/opt/Primo.AI/IDP/start_evaluation.sh"
},

Запуск службы:
[primo-admin@astra-machine ~]$ sudo systemctl start Primo.AI.Agent
Просмотр статуса службы:
[primo-admin@astra-machine ~]$ sudo systemctl status Primo.AI.Agent
Просмотр журнала службы:
[primo-admin@astra-machine ~]$ sudo journalctl -u Primo.AI.Agent
Настройка правила брандмауэра ufw
Установка и настройка брандмауэра ufw описана в статье Межсетевой экран ufw .
Для разрешения доступа к API агента выполните следующее:
[primo-admin@astra-machine ~]$ sudo ufw allow 5002/tcp
Настройка учетной записи IDP
Создание учётной записи IDP idp:
[primo-admin@astra-machine ~]$ sudo useradd -g primo-ai -m -s /bin/bash idp
Установка пароля учётной записи IDP idp:
[primo-admin@astra-machine ~]$ sudo passwd idp
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён
Обновление агента
Остановка службы:
[primo-admin@astra-machine ~]$ sudo systemctl stop Primo.AI.Agent

Обновление файлов агента на Целевой машине (файл Agent-linux.zip должен находиться в каталоге /srv/samba/shared/install):
[primo-admin@astra-machine ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json

[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent

[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent 

[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent

Запуск службы:
[primo-admin@astra-machine ~]$ sudo systemctl start Primo.AI.Agent

Просмотр статуса службы:
[primo-admin@astra-machine ~]$ sudo systemctl status Primo.AI.Agent

Настройка пользователей и групп
Эти команды необходимо выполнять от имени пользователя, настроенного как администратор при установке Astra Linux:
[admin@astra-machine ~]$ sudo systemctl stop Primo.AI.Agent

[admin@astra-machine ~]$ sudo useradd -m -s /bin/bash primo-admin

[admin@astra-machine ~]$ sudo passwd primo-admin
Новый пароль : ***
Повторите ввод нового пароля : ***
passwd: пароль успешно обновлён

Теперь войдите в систему под пользователем primo-admin и дальнейшие команды выполняйте под его именем.
Выполните команды из следующих разделов:
•	Настройка дополнительного ПО
•	Настройка учетной записи агента
Существующие учётные записи IDP добавьте в группу primo-ai:
[primo-admin@astra-machine ~]$ sudo usermod -G primo-ai robot

Обновление агента и файла конфигурации
Обновление файлов агента (файл Agent-linux.zip должен находиться в каталоге /srv/samba/shared/install):
[primo-admin@astra-machine ~]$ sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /opt/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json
[primo-admin@astra-machine ~]$ sudo chown -R agent.primo-ai /opt/Primo.AI/Agent
[primo-admin@astra-machine ~]$ sudo chmod -R g+w /opt/Primo.AI/Agent 
[primo-admin@astra-machine ~]$ sudo chmod a+x /opt/Primo.AI/Agent/Primo.AI.Agent


Обновление файла управления службой

[primo-admin@astra-machine ~]$ sudo cp /opt/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
[primo-admin@astra-machine ~]$ sudo systemctl daemon-reload
[primo-admin@astra-machine ~]$ sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service

