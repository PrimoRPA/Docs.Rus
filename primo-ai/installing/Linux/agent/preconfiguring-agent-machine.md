# Настройка целевой машины 

## Предполагаемая аудитория 

Раздел предназначен для системных администраторов со следующими навыками:
1. Обязательно – уверенный пользователь ОС Linux:
   *	владеет основными командами для перемещения в папках и файлах;
   *	умеет создавать и редактировать текстовые файлы;
   *	умеет копировать файлы, текст из файлов, сохранять файлы.
1. Обязательно – опыт администрирования ОС Linux:
   * умеет запускать программы и скрипты;
   * имел опыт работы c bash;
   * имел опыт сетевого и системного администрирования ОС Linux.

## Системные требования
Для целевой машины следует использовать рабочую станцию под управлением Astra Linux, к которой предъявляются требования из таблицы ниже.

| Параметр        | Требование                     | 
| --------------- | ------------------------------ | 
| CPU             | 4 физических ядра	/ 8 виртуальных ядер | 
| RAM             | 8 Гб	                          |  
| HDD             | 250 Гб (OS + Data)	            |  

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — их вы найдете в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл            | Описание                              | Примечание   |
| --------------- | ------------------------------------- | ------------ |
| Agent-linux.zip | Дистрибутив агента	                  |  |
| A-IDP.zip       | Дистрибутив IDP	 | Вариант установки А: <p> -	при наличии интернета; </p> <p> -	python 3.10+; </p><p> -	GNU C Library (glibc) версии 2.33 и выше </p> |
| B-IDP.zip       | Дистрибутив IDP	 | Вариант установки Б – при невозможности выполнить вариант установки А |
| B-pyenv.zip     | Вспомогательное ПО – pyenv со встроенным Python 3.11  | Вариант установки Б – при невозможности выполнить вариант установки А |


## Введение

Компоненты Primo.AI.Api (выборочно) и их связи приведены на схеме ниже:

![Компоненты Primo.AI.Api и целевые машины](<../../../../.gitbook/assets1/primo-ai/install/components-and-machines-scheme.png>)

**Агент** – self-hosted веб-приложение, REST API. Агент выполнен как NET8-приложение, которое устанавливается на целевой машине и используется для управления IDP.

**IDP** – data science-ядро с нейронными сетями и OCR. Предназначено для интеллектуальной обработки документов. Размещено на специальным образом настроенной целевой машине.

На одной целевой машине может работать только один агент – это ограничение обусловлено полной нагрузкой машины IDP-процессом. Целевых машин может быть много. Все целевые машины должны быть настроены одинаково, и на каждой целевой машине должен быть развернут агент. Версии ОС на целевых машинах могут отличаться

Порт `44392`, указанный на схеме выше, используется при настройке конфигурационных файлов агента и открытия портов на файерволе (в том числе аппаратном в сети организации). 

Для настройки целевой машины нужна чистая  машина с ОС Linux (обязательно с последними обновлениями). На машину необходимо скопировать папку с комплектом поставки. Это может быть любая папка, но для определенности пусть будет папка `/srv/samba/shared/install`*.

Для настройки целевой машины требуется последовательно выполнить все шаги настоящего руководства.

> \**Сетевая папка, доступная с машины, на которой размещен комплект поставки.* 

## Подготовка к установке

При установке Astra Linux на целевой машине необходимо создать пользователя-администратора. Для этого на экране «Настройка учетных записей и паролей» введите имя `primo-admin` для учетной записи администратора.

![Настройка учетных записей и паролей](<../../../../.gitbook/assets1/primo-ai/install/create-admin-user.png>)

Установка дополнительного ПО и создание дополнительных пользователей описаны ниже.

## Настройка дополнительного ПО

Выполните подключение целевой машины к репозиториям `main`, `update`, `base` и `extended`. Сами репозитории описаны в статье [Интернет-репозитории Astra Linux Special Edition x.7](https://wiki.astralinux.ru/pages/viewpage.action?pageId=158598882). Настройка локальных зеркал этих репозиториев описана в статье [Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте](https://wiki.astralinux.ru/pages/viewpage.action?pageId=199148426).

:large_orange_diamond:***Важно**. Локальные репозитории необходимо выгружать на машине, имеющей доступ в интернет.*

Рекомендуется выделить одну машину под управлением Astra Linux для размещения на ней сервера репозиториев.

Проверьте доступность репозиториев, используя команду: 
```
# sudo apt update
```
Репозитории `main`, `update`, `base` и `extended` должны присутствовать в выводе команды.


## Агент

### Настройка учетной записи агента

Для работы агента и IDP создайте общую группу:
```
# sudo groupadd primo-ai
```
Для работы агента создайте учетную запись **agent**:
```
# sudo useradd -g primo-ai -m -s /bin/bash agent
```

### Установка агента

Разверните файлы агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`): 
```
# sudo mkdir -p /app/Primo.AI /app/Primo.AI/Agent /app/Primo.AI/AgentData 
# sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /app/Primo.AI/Agent
# sudo chmod –R 771 /app/Primo.AI/Agent /app/Primo.AI/AgentData
# sudo chown -R agent:primo-ai /app/Primo.AI/Agent /app/Primo.AI/AgentData /app/Primo.AI/Agent
```

Для запуска и остановки агентом IDP-ядра без ввода пароля установите следующую настройку:
```
# sudo sh -c "echo 'agent ALL=(%primo-ai) NOPASSWD: /app/Primo.AI/Agent/kill.sh, /app/Primo.AI/IDP/start_inference.sh, /app/Primo.AI/IDP/start_training.sh, /app/Primo.AI/IDP/start_evaluation.sh' > /etc/sudoers.d/Primo.AI.Agent"
```

Установите агент как службу и настройте автозапуск:
```
# sudo cp /app/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
# sudo systemctl daemon-reload
# sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```

В конфигурационном файле `appsettings.ProdLinux.json` укажите адрес Primo.AI.Api и его компонентов, а также TenantId (если эта машина не в тенанте по умолчанию) и пользователя тенанта:
```
 	"Api": {
    		"UserName": "agent",
    		"Password": "Xxxxxxxxxxxx",

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
  "ProcessFileName": "/app/Primo.AI/IDP/start_training.sh"
},
"InferenceProcess": {
  "ProcessFileName": "/app/Primo.AI/IDP/start_inference.sh"
},
"TestProcess": {
  "ProcessFileName": "/app/Primo.AI/IDP/start_evaluation.sh"
},
```

Запустите службы:
```
# sudo systemctl start Primo.AI.Agent
```

Проверьте статус службы:
```
# sudo systemctl status Primo.AI.Agent
```

Просмотрите журнал службы:
```
# sudo journalctl -u Primo.AI.Agent
```

### Настройка правила брандмауэра ufw

Для разрешения доступа к API агента выполните команду:
```
# sudo ufw allow 5002/tcp
```


## IDP
### Вариант установки А

> Установка IDP при наличии в репозиториях apt целевой машины python3.10/3.11, выхода в интернет, а также GNU C Library (glibc) версии 2.33 и выше.

Создайте учетную запись **idp**:
```
# sudo useradd -g primo-ai -m -s /bin/bash idp
```

Разверните файлы IDP на целевой машине (файл `A-IDP.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
# sudo mkdir -p /app/Primo.AI/IDP 
# sudo unzip /srv/samba/shared/install/A-IDP.zip -d /app/Primo.AI/IDP
# sudo chmod –R 771 /app/Primo.AI/IDP
# sudo chown -R idp:primo-ai /app/Primo.AI/IDP
```

Установите библиотеки python3, tesseract и другие пакеты:
```
# apt-get update & apt install python3=3.11 python3-venv=3.11 libsm6 libxext6 tesseract-ocr build-essential libssl-dev libffi-dev python3-dev ffmpeg
```

Создайте и активируйте виртуальную среду venv:
```
# python3 –m venv /app/Primo.AI/IDP/venv

# source /app/Primo.AI/IDP/venv/bin/activate
```

Установите пакеты python. 
```
# python -m ensurepip –upgrade
```

*	Если для IDP-процесса будет использоваться CPU:
```
# pip3 install –r /app/Primo.AI/IDP/prequisites_cpu.txt
# pip3 install –r /app/Primo.AI/IDP/requirements_cpu.txt
```
*	Если для IDP-процесса будет использоваться GPU:
```
# pip3 install –r /app/Primo.AI/IDP/prequisites.txt	
# pip3 install –r /app/Primo.AI/IDP/requirements.txt
```

Произведите финальную раздачу прав IDP:
```
# sudo chmod –R 771 /app/Primo.AI/IDP
# sudo chown -R idp:primo-ai /app/Primo.AI/IDP
```

### Вариант установки Б

> Используйте этот способ при отсутствии необходимых библиотек.

Создайте учетную запись **idp**, указав расположение home-папки – в ней будут размещены инсталляции Python, а также все необходимые пакеты суммарным весом более 3.5 Гбайт:
```
# sudo useradd -g primo-ai -m -s /bin/bash -d <custom_home_dir_location> idp
```

#### Установка pyenv c Python 3.11 и виртуальной средой

Создайте временный каталог `pyenv` и переместитесь туда: 
```
# mkdir pyenv
# cd pyenv 
```
Скопируйте во временный каталог файлы pyenv из комплекта поставки (файл `B-pyenv.zip` должен находиться в каталоге `/srv/samba/shared/install`): 
```
# sudo unzip /srv/samba/shared/install/B-pyenv.zip . 
```

Запустите скрипт установки `pyenv-installer.sh`: 
```
# sudo ./pyenv-installer.sh idp primo-ai  <custom_home_dir_location>
```

Сообщение *«WARNING: The Python tkinter extension was not compiled and GUI subsystem has been detected. Missing the Tk toolkit?»* можно проигнорировать.

Удалите установочные файлы: 
```
# sudo rm  pyenv-installer.sh B-pyenv.zip Python-3.11.9.tar.xz
```

#### Установка зависимостей IDP в виртуальную среду

Создайте папку с инсталляцией:
```
# mkdir /app/Primo.AI/IDP
```

Распакуйте архив с IDP в каталог `/app/Primo.AI/IDP` (файл `B-IDP.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
# sudo unzip /srv/samba/shared/install/B-IDP.zip -d /app/Primo.AI/IDP
```

Переместитесь в папку с инсталляцией:
```
# cd /app/Primo.AI/IDP
```
Запустите скрипт установки `idp-installer.sh`:
```
# sudo ./idp-installer.sh idp primo-ai <custom_home_dir_location>
```

Раздайте права на IDP:
```
# sudo chmod –R 771 /app/Primo.AI/IDP
# sudo chown -R idp:primo-ai /app/Primo.AI/IDP
```
Удалите установочные файлы: 
```
# sudo rm /app/Primo.AI/IDP/idp-installer.sh /app/Primo.AI/IDP/venv.zip 
```

#### Установка Tesseract

Проверьте наличие Tesseract версии 4.0.0+: 
```
# sudo apt policy tesseract-ocr
tesseract-ocr: 
 Установлен:                   (отсутствует) 
 Кандидат:   4.0.0-2~bpo9+1
```

Установите Tesseract:
```
# sudo apt install tesseract-ocr
```

 

## Проверка настройки целевой машины

Проверьте доступность Primo.AI.Api с целевой машины. На целевой машине выполните команду:
```
# curl -k https://<IP-адрес-Primo.Ai.Api>:44392/api/version
```
Убедитесь, что вернулась версия Primo.Ai.Api.

Проверьте работу агента на целевой машине. На машине Primo.Ai.Api выполните команду:
```
# curl -k https://<IP-адрес-целевой-машины>:5002/api/version
```
Убедитесь, что вернулась версия агента.

## Ограничение нагрузки 

Оптимальная нагрузка на целевую машину предполагает размещение единственного агента с IDP-ядром и запуск единственного в каждый момент времени процесса любого типа – обучение или инференс (распознавание изображений в IDP).

Кроме того, для процессов инференса следует ограничивать единовременное количество запросов (изображений) в обработке. Превышение этого ограничения приведет к неадекватному кратному увеличению времени обработки изображений. 

Рассчитайте максимальную нагрузку на целевую машину по формуле: **0.5n – 1**, где **n** – количество виртуальных ядер процессора (например, для 16 виртуальных ядер это значение – 7).

Пропишите итоговое значение в параметре **InferenceRequestQueue** -> **MaxImagesLoad** в конфигурационном файле агента (`appsettings.ProdLinux.json`):

![](<../../../../.gitbook/assets1/primo-ai/install/agent/install-agent-and-idp-1.png>)
