# Порядок установки Оркестратора и его компонентов

Primo RPA Orchestrator (далее в тексте - Orchestrator, Оркестратор) может быть установлен на операционных системах семейств Windows (Windows 2019 Server, Windows 2016 Server) и Linux (Astra Linux 1.7, Cent OS 8, РЕДОС).

В данной статье содержатся следующие разделы:

1. Установка компонентов Оркестратора на ОС Linux
2. Установка компонентов Оркестратора на ОС Windows
3. Пошаговые инструкции по установке Оркестратора
4. Установка робота

Развертывание Оркестратора подразумевает последовательную установку двух подсистем: 
* Оркестратора;
* Робота.

Все шаги самодостаточны, содержат установку необходимых переменных окружения, открытия [портов](http://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/install-ports) на файерволе ОС, настройку прав и т.п.

### Условия для корректной работы
1. **Windows**. Службы устанавливаются под администратором и работают под LocalSystem.
2. **Linux**. Службы устанавливаются и работают от root.
3. **Учетные записи**. На машинах Оркестратора и БД используются только для поддержки и администрирования системы.
4. **Права учетной записи в БД**. Должна иметь права на чтение/вставку/изменение/удаление записей таблиц и создание объектов БД - для возможности автоматических миграций.

> Если у вас существуют сложности или ограничения со скачиванием необходимых компонентов с сайтов их официальных поставщиков, вы можете скачать в виде единого архива для Оркестратора.
> Актуальную ссылку для скачивания можно найти в разделе [Что нового - Orchestrator](https://docs.primo-rpa.ru/primo-rpa/release-notes/orch).

## Установка компонентов Оркестратора на ОС Linux

В общем виде, развертывание Оркестратора предполагает установку следующих компонентов в указанном порядке:

1. [Предварительная настройка машины Оркестратора под Cent OS](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/setting-up-machines-linux/presetting-orch-machine-linux)

2. Установка **PostgreSQL** - Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/). Затем выполните шаги по подключению по сети и созданию пользователей согласно статье [**Установка PostgreSQL под CentOS 8**](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/postgres-centos).

3. Установка **RabbitMQ** - Скачайте и установите нужную версию, используя инструкции для [Debian, Ubuntu и основанных на них дистрибутивах](https://www.rabbitmq.com/docs/install-debian), либо инструкции для [RPM дистрибутивов](https://www.rabbitmq.com/docs/install-rpm).  
Далее следуйте инструкции, описанной в статье [Установка RabbitMQ под CentOS 8](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/rabbitmq-centos).

4. Установка **nginx** - установите nginx из репозиториев. Подробно установка nginx описана в документе [Установка Nginx под CentOS 8](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/nginx-centos).

5. Установка **UI** - общий порядок установки UI (на примере CentOS 8) описан в документе [Установка UI под CentOS 8](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/ui-centos).

6. Установка **WebApi** - описание процесса установки (на примере Cеnt OS 8) находится в документе [Руководство по установке WebApi](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/webapi-centos)

> **Дальнейшие пункты (6-10) могут выполняться в произвольном порядке.**

7. Установка **RDP2** - информацию об установке RDP2 на машине с ОС Astra Linux 1.7 и CentOS 8 можно найти в соответствующих документах: [Руководство по установке RDP2 под Astra Linux 1.7](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/astra/RDP2-astra) и [Руководство по установке RDP2 под CentOS 8](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/rdp2-centos).

8. Установка **States** - выполните установку службы согласно [инструкции по установке](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/states-centos).

9. Установка **RobotLogs** - процесс установки данной службы описан в статье [Установка RobotLogs под CentOS 8](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/robotlogs-centos).

10. Установка **Notifications** - установите службу, следуя [инструкции](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/notifications-centos).

11. Установка **MachineInfo** - порядок установки MachineInfo описан в [данной статье](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/centos/machineinfo-centos)



## Установка компонентов Оркестратора на ОС Windows

В общем виде процедура установки компонентов Оркестратора на операционной системе Windows аналогична процедуре для ОС Linux и предполагает выполнение указанных ниже шагов.

Существует два варианта установки Оркестратора на ОС Windows: с использованием nginx и с использованием IIS. 
Кроме того, возможно использование как PostgreSQL, так и MSSQL.

Порядок установки:

1. [Предварительная настройка машины Оркестратора на Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/setting-up-machines-win/presetting-orch-machine-win).

2. Установка **PostgreSQL** либо **MSSQL**. 
    * Для PostgreSQL: Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/). Затем выполните шаги по подключению по сети и созданию пользователей согласно статье [**Установка PostgreSQL под Windows 2016 Server**](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/postgres-windows).
    * Для MSSQL: Установите версию, соответствующую имеющейся у вашей компании лицензии. Выполните специфические настройки, описанные в [статье](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/mssql-windows)  

3. Установка **RabbitMQ** - Скачайте и установите нужную версию, используя инструкции для [установки под Windows](https://www.rabbitmq.com/docs/install-windows).  
Далее следуйте инструкции, описанной в статье [Установка RabbitMQ под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/rabbitmq-windows).

4. Установка **UI** и **WebApi** для **nginx** или **IIS**.
    * Для nginx: [Скачайте](https://nginx.org/ru/download.html) и установите nginx. Также ознакомьтесь с информацией на [сайте продукта](https://nginx.org/ru/docs/windows.html).
    После установки выполните действия, [описанные в инструкции](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/nginx-windows).   
    Для установки UI используйте статью [Установка UI на nginx](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/ui-nginx-windows).  
    Порядок установки WebApi описан в статье [Установка WebApi](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/webapi-windows).  
    * Для IIS: Используйте инструкцию [Установка WebApi и UI на IIS под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/webapi-ui-iis-windows).

5. Установка **RDP2** - подробная информация о процедуре установки приведена в [инструкции](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/rdp2-windows).

6. Установка **States** - выполните установку в соответствии с инструкцией в статье [Установка States под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/states-windows).

7. Установка **RobotLogs** - порядок установки RobotLogs описан в [инструкции](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/robotlogs-windows).

8. Установка **Notifications** - описание процесса установки можно найти в статье [Установка Notifications под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/notifications-windows).

9. Установка **MachineInfo** - для установки воспользуйтесь [данной инструкцией](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/machineinfo-windows).


## Установка Оркестратора: пошаговые инструкции

Инструкцию по установке Оркестратора на Windows Server 2019 с WebApi (IIS) можно найти [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/quick-install/iis-web-server). Доступна также видео-инструкция: [Установка Оркестратора в 8 шагов за полчаса (IIS)](https://rutube.ru/video/9bb248ccced157536cbf8af50b038012/).

Также можно ознакомиться со статьей по [установке Оркестратора на веб-сервер Nginx](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/quick-install/nginx-web-server), либо ее [видео-версией](https://rutube.ru/video/53ac25d2c3128bdd6cea7d055e88255b/).

Процедура установки Оркестратора на операционной системе Linux (на примере Ubuntu Server 22.04) описана в статье [Установка Primo RPA Orchestrator на Ubuntu Server 22.04](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/install-on-ubuntu).


## Установка Робота

После установки Оркестратора можно переходить к установке Робота. 

Последовательно выполните шаги из таблицы.

| Шаг                                              | Примечание     |
| ------------------------------------------------ | -------------- |
| 1. Настройка машины робота                       | 1. См. [Настройка машины робота под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/setting-up-machines-win/presetting-robot-machine-win) <p>2. См. [Настройка машины робота](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/setting-up-machines-linux/presetting-robot-machine-linux) </p> |  
| 2. Установка Agent на машине робота              | 1. См. [Установка Агента Оркестратора под Windows 2016 Server](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/windows/setting-up-machines-win/appendix-win). <p> 2. См. [Установка Агента Оркестратора](https://docs.primo-rpa.ru/primo-rpa/orchestrator-new/install/linux/setting-up-machines-linux/agentinstall) </p> |  

### Условия для корректной работы

1. **Windows**. Используйте на машине робота одну учетную запись для службы Агента Оркестратора. Она нужна, чтобы Агент смог проделать предварительную работу по запуску Робота и создать задачу в Windows, которая запустит Робота.
2. **Linux**. Требуется одна учетная запись для функционирования Агента Оркестратора.
