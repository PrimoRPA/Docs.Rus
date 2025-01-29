# Порядок установки Оркестратора и его компонентов

Primo RPA Orchestrator (далее в тексте - Orchestrator, Оркестратор) может быть установлен на операционных системах семейств Windows (Windows 2019 Server, Windows 2016 Server) и Linux (Astra Linux 1.7, Cent OS 8, РЕДОС).

В данной статье содержатся следующие разделы:

1. [Установка компонентов Оркестратора на ОС Linux](https://azure-dos.s1.primo1.orch/PrimoCollection/Documentation/_git/Documentation.RU?path=/orchestrator-new/install/install-overview.md&version=GBOrch-NewDocs-OrchMachineRobotMachine&_a=preview&anchor=%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0-%D0%BD%D0%B0-%D0%BE%D1%81-linux)
2. [Установка компонентов Оркестратора на ОС Windows](https://azure-dos.s1.primo1.orch/PrimoCollection/Documentation/_git/Documentation.RU?path=/orchestrator-new/install/install-overview.md&version=GBOrch-NewDocs-OrchMachineRobotMachine&_a=preview&anchor=%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-%D0%BA%D0%BE%D0%BC%D0%BF%D0%BE%D0%BD%D0%B5%D0%BD%D1%82%D0%BE%D0%B2-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0-%D0%BD%D0%B0-%D0%BE%D1%81-windows)
3. [Пошаговые инструкции по установке Оркестратора](https://azure-dos.s1.primo1.orch/PrimoCollection/Documentation/_git/Documentation.RU?path=/orchestrator-new/install/install-overview.md&version=GBOrch-NewDocs-OrchMachineRobotMachine&_a=preview&anchor=%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-%D0%BE%D1%80%D0%BA%D0%B5%D1%81%D1%82%D1%80%D0%B0%D1%82%D0%BE%D1%80%D0%B0%3A-%D0%BF%D0%BE%D1%88%D0%B0%D0%B3%D0%BE%D0%B2%D1%8B%D0%B5-%D0%B8%D0%BD%D1%81%D1%82%D1%80%D1%83%D0%BA%D1%86%D0%B8%D0%B8)
4. [Установка робота](https://azure-dos.s1.primo1.orch/PrimoCollection/Documentation/_git/Documentation.RU?path=/orchestrator-new/install/install-overview.md&version=GBOrch-NewDocs-OrchMachineRobotMachine&_a=preview&anchor=%D1%83%D1%81%D1%82%D0%B0%D0%BD%D0%BE%D0%B2%D0%BA%D0%B0-%D1%80%D0%BE%D0%B1%D0%BE%D1%82%D0%B0)

Развертывание Оркестратора подразумевает последовательную установку двух подсистем: 
* Оркестратора;
* Робота.

Все шаги самодостаточны, содержат установку необходимых переменных окружения, открытия [портов](../../orchestrator-new/install/install-ports.md) на файерволе ОС, настройку прав и т.п.

### Условия для корректной работы
1. **Windows**. Службы устанавливаются под администратором и работают под LocalSystem.
2. **Linux**. Службы устанавливаются и работают от root.
3. **Учетные записи**. На машинах Оркестратора и БД используются только для поддержки и администрирования системы.
4. **Права учетной записи в БД**. Должна иметь права на чтение/вставку/изменение/удаление записей таблиц и создание объектов БД - для возможности автоматических миграций.

> Если у вас существуют сложности или ограничения со скачиванием необходимых компонентов с сайтов их официальных поставщиков, вы можете скачать в виде единого архива для Оркестратора.
> Актуальную ссылку для скачивания можно найти в разделе [Что нового - Orchestrator](https://docs.primo-rpa.ru/primo-rpa/release-notes/orch).

## Установка компонентов Оркестратора на ОС Linux

В общем виде, развертывание Оркестратора предполагает установку следующих компонентов в указанном порядке:

1. [Предварительная настройка машины Оркестратора под Cent OS](../../../orchestrator-new/install/linux/setting-up-machines-linux/presetting-orch-machine-linux.md)

2. Установка **PostgreSQL** - Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/). Затем выполните шаги по подключению по сети и созданию пользователей согласно статье [**Установка PostgreSQL под CentOS 8**](../../../orchestrator-new/install/linux/centos/postgres-centos.md).

3. Установка **RabbitMQ** - Скачайте и установите нужную версию, используя инструкции для [Debian, Ubuntu и основанных на них дистрибутивах](https://www.rabbitmq.com/docs/install-debian), либо инструкции для [RPM дистрибутивов](https://www.rabbitmq.com/docs/install-rpm).  
Далее следуйте инструкции, описанной в статье [Установка RabbitMQ под CentOS 8](../../../orchestrator-new/install/linux/centos/rabbitmq-centos.md).

4. Установка **nginx** - установите nginx из репозиториев. Подробно установка nginx описана в документе [Установка Nginx под CentOS 8](../../../orchestrator-new/install/linux/centos/nginx-centos.md).

5. Установка **UI** - общий порядок установки UI (на примере CentOS 8) описан в документе [Установка UI под CentOS 8](../../../orchestrator-new/install/linux/centos/ui-centos.md).

6. Установка **WebApi** - описание процесса установки (на примере Cеnt OS 8) находится в документе [Руководство по установке WebApi](../../../rchestrator-new/install/linux/centos/webapi-centos.md)

> **Дальнейшие пункты (6-10) могут выполняться в произвольном порядке.**

7. Установка **RDP2** - информацию об установке RDP2 на машине с ОС Astra Linux 1.7 и CentOS 8 можно найти в соответствующих документах: [Руководство по установке RDP2 под Astra Linux 1.7](../../../orchestrator-new/install/linux/astra/RDP2-astra.md) и [Руководство по установке RDP2 под CentOS 8](orchestrator-new/install/linux/centos/rdp2-centos.md).

8. Установка **States** - выполните установку службы согласно [инструкции по установке](../../../orchestrator-new/install/linux/centos/states-centos.md).

9. Установка **RobotLogs** - процесс установки данной службы описан в статье [Установка RobotLogs под CentOS 8](../../../orchestrator-new/install/linux/centos/robotlogs-centos.md).

10. Установка **Notifications** - установите службу, следуя [инструкции](../../../orchestrator-new/install/linux/centos/notifications-centos.md).

11. Установка **MachineInfo** - порядок установки MachineInfo описан в [данной статье](../../../orchestrator-new/install/linux/centos/machineinfo-centos.md)



## Установка компонентов Оркестратора на ОС Windows

В общем виде процедура установки компонентов Оркестратора на операционной системе Windows аналогична процедуре для ОС Linux и предполагает выполнение указанных ниже шагов.

Существует два варианта установки Оркестратора на ОС Windows: с использованием nginx и с использованием IIS. 
Кроме того, возможно использование как PostgreSQL, так и MSSQL.

Порядок установки:

1. [Предварительная настройка машины Оркестратора на Windows 2016 Server](../../../orchestrator-new/install/windows/setting-up-machines-win/presetting-orch-machine-win.md).

2. Установка **PostgreSQL** либо **MSSQL**. 
    * Для PostgreSQL: Скачайте и установите соответствующую вашей операционной системе версию, используя [инструкцию](https://www.postgresql.org/download/). Затем выполните шаги по подключению по сети и созданию пользователей согласно статье [**Установка PostgreSQL под Windows 2016 Server**](../../orchestrator-new/install/windows/postgres-windows.md).
    * Для MSSQL: Установите версию, соответствующую имеющейся у вашей компании лицензии. Выполните специфические настройки, описанные в [статье](../../orchestrator-new/install/windows/mssql-windows.md)  

3. Установка **RabbitMQ** - Скачайте и установите нужную версию, используя инструкции для [установки под Windows](https://www.rabbitmq.com/docs/install-windows).  
Далее следуйте инструкции, описанной в статье [Установка RabbitMQ под Windows 2016 Server](../../orchestrator-new/install/windows/rabbitmq-windows.md).

4. Установка **UI** и **WebApi** для **nginx** или **IIS**.
    * Для nginx: [Скачайте](https://nginx.org/ru/download.html) и установите nginx. Также ознакомьтесь с информацией на [сайте продукта](https://nginx.org/ru/docs/windows.html).
    После установки выполните действия, [описанные в инструкции](../../orchestrator-new/install/windows/nginx-windows.md).   
    Для установки UI используйте статью [Установка UI на nginx](../../orchestrator-new/install/windows/ui-nginx-windows.md).  
    Порядок установки WebApi описан в статье [Установка WebApi](../../orchestrator-new/install/windows/webapi-windows.md).  
    * Для IIS: Используйте инструкцию [Установка WebApi и UI на IIS под Windows 2016 Server](../../orchestrator-new/install/windows/webapi-ui-iis-windows.md).

5. Установка **RDP2** - подробная информация о процедуре установки приведена в [инструкции](../../orchestrator-new/install/windows/rdp2-windows.md).

6. Установка **States** - выполните установку в соответствии с инструкцией в статье [Установка States под Windows 2016 Server](../../orchestrator-new/install/windows/states-windows.md).

7. Установка **RobotLogs** - порядок установки RobotLogs описан в [инструкции](../../orchestrator-new/install/windows/robotlogs-windows.md).

8. Установка **Notifications** - описание процесса установки можно найти в статье [Установка Notifications под Windows 2016 Server](../../orchestrator-new/install/windows/notifications-windows.md).

9. Установка **MachineInfo** - для установки воспользуйтесь [данной инструкцией](../../orchestrator-new/install/windows/machineinfo-windows.md).


## Установка Оркестратора: пошаговые инструкции

Видео по установке Оркестратора на Windows Server 2019 с WebApi (IIS) можно просмотреть здесь:  [**Установка Оркестратора в 8 шагов за полчаса (IIS)**](https://rutube.ru/video/9bb248ccced157536cbf8af50b038012/).

Также можно ознакомиться с видеороликом по [**установке Оркестратора на веб-сервер Nginx**](https://rutube.ru/video/53ac25d2c3128bdd6cea7d055e88255b/).

Процедура установки Оркестратора на операционной системе Linux (на примере Ubuntu Server 22.04) описана в статье [**Установка Primo RPA Orchestrator на Ubuntu Server 22.04**](../../orchestrator-new/install/linux/install-on-ubuntu.md).


## Установка Робота

После установки Оркестратора можно переходить к установке Робота. 

Последовательно выполните шаги из таблицы.

| Шаг                                              | Примечание     |
| ------------------------------------------------ | -------------- |
| 1. Настройка машины робота                       | 1. См. [Настройка машины робота под Windows 2016 Server](../../orchestrator-new/install/windows/setting-up-machines-win/presetting-robot-machine-win.md) <p>2. См. [Настройка машины робота](../../orchestrator-new/install/linux/setting-up-machines-linux/presetting-robot-machine-linux.md) </p> |  
| 2. Установка Agent на машине робота              | 1. См. [Установка Агента Оркестратора из инсталлятора под Windows 2016 Server](../../orchestrator-new/install/windows/setting-up-machines-win/agentinstaller-win.md) или [Установка Агента без инсталлятора под Windows 2016 Server](../../orchestrator-new/install/windows/setting-up-machines-win/appendix-win.md). <p> 2. См. [Установка Агента Оркестратора](../../orchestrator-new/install/linux/setting-up-machines-linux/agentinstall.md) </p> |  

### Условия для корректной работы

1. **Windows**. Используйте на машине робота одну учетную запись для службы Агента Оркестратора. Она нужна, чтобы Агент смог проделать предварительную работу по запуску Робота и создать задачу в Windows, которая запустит Робота.
2. **Linux**. Требуется одна учетная запись для функционирования Агента Оркестратора.