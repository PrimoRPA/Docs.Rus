# Установка без использования Docker

## Выбор варианта установки

Выберите подходящий вариант установки программных компонентов на целевую машину без использования Docker.

| Вариант установки | Нужен интернет | Нужен glibc 2.33+ | Нужен менеджер пакетов apt | Нужна чистая ОС                                 |
| ----------------- | -------------- | ----------------- | -------------------------- | ----------------------------------------------- |
| A                 | Да             | Да                | Да                         | Нет                                             |
| B                 | Нет            | Нет               | Да                         | Нет                                             |
| C                 | Нет            | Нет               | Нет                        | Astra Linux Special Edition 1.7 (базовая) amd64 |

В остальных случаях рекомендуется запускать целевую машину в виде docker-контейнера. 

## Файлы из комплекта поставки

Cкопируйте на целевую машину файлы из комплекта поставки Primo RPA AI Server в соответствии с выбранным вариантом установки. Остальное ПО должно быть предустановлено в Astra Linux.


{% tabs %}

{% tab title="Вариант установки A" %} 

**Файлы из комплекта поставки**: 
* `Agent-linux.zip` — дистрибутив агента.
* `A-IDP.zip` — дистрибутив IDP.

**Требует наличия**:
* GNU C Library (glibc) версии 2.33 и выше — для компиляции вспомогательных библиотек.
* `software-properties-common` — пакет для менеджера apt.

{% endtab %}

{% tab title="Вариант установки B" %} 

**Файлы из комплекта поставки**: 
* `Agent-linux.zip` — дистрибутив агента.
* `B-IDP.zip` — дистрибутив IDP.
* `B-pyenv.zip`— вспомогательное ПО для варианта установки B. Содержит pyenv со встроенным Python 3.11.

**Требуются зависимости**:

{% code title="" overflow="wrap" lineNumbers="true" %}

```
make build-essential libssl-dev zlib1g-dev libbz2-dev libreadline-dev libsqlite3-dev wget curl llvm libedit-dev libncursesw5-dev xz-utils tk-dev libxml2-dev libxmlsec1-dev libffi-dev liblzma-dev
```

{% endcode %}

{% endtab %}


{% tab title="Вариант установки C" %} 


**Файлы из комплекта поставки**: 
* `Agent-linux.zip` — дистрибутив агента.
* `C-IDP.zip` — дистрибутив IDP.
* `C-pkgs.zip`— вспомогательное ПО для варианта установки C. Содержит .deb-пакеты с Python 3.11, venv, ffmpeg, tesseract-ocr.


{% endtab %}

{% endtabs %}



## Подготовка к установке

При установке Astra Linux на целевой машине необходимо создать пользователя-администратора. Для этого на экране «Настройка учетных записей и паролей» введите имя `primo-admin` для учетной записи администратора.

![Настройка учетных записей и паролей](<../../../../.gitbook/assets1/primo-ai/install/create-admin-user.png>)

Установка дополнительного ПО и создание дополнительных пользователей описаны ниже.

## Настройка дополнительного ПО

{% hint style="info" %}
Если вы выбрали вариант установки С, то выполнять эту настройку не нужно.
{% endhint %}

Выполните подключение целевой машины к репозиториям `main`, `update`, `base` и `extended`. В этом вам могут помочь статьи:
* [Интернет-репозитории Astra Linux Special Edition x.7](https://wiki.astralinux.ru/pages/viewpage.action?pageId=158598882).
* [Создание репозиториев для операционной системы Astra Linux Special Edition x.7 в закрытом сегменте](https://wiki.astralinux.ru/pages/viewpage.action?pageId=199148426) — описывает настройку локальных зеркал данных репозиториев.

{% hint style="warning" %}
Локальные репозитории необходимо выгружать на машине, имеющей доступ в интернет.
{% endhint %}

Рекомендуется выделить одну машину под управлением Astra Linux для размещения на ней сервера репозиториев.

Проверьте доступность репозиториев, используя команду: 
```
sudo apt update
```
Репозитории `main`, `update`, `base` и `extended` должны присутствовать в выводе команды.

## Установка агента

Установка агента осуществляется одинаково для любого из вариантов установки.

### Настройка учетной записи 

Для работы агента и IDP создайте общую группу:
```
sudo groupadd primo-ai
```
Для работы агента и IDP-ядра создайте учетную запись **agent**, указав расположение home-папки – в ней будут размещены инсталляции Python, а также все необходимые пакеты **суммарным весом более 3.5 Гбайт** (при установке IDP-ядра с использованием "варианта Б" - см. далее):
```
sudo useradd -g primo-ai -m -s /bin/bash -d <custom_home_dir_location> agent
```

### Установка агента

Разверните файлы агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`): 
```
sudo mkdir -p /app/Primo.AI /app/Primo.AI/Agent /app/Primo.AI/AgentData 
```
```
sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /app/Primo.AI/Agent
```
```
sudo chmod -R 771 /app/Primo.AI/Agent /app/Primo.AI/AgentData
```
```
sudo chown -R agent:primo-ai /app/Primo.AI/Agent /app/Primo.AI/AgentData /app/Primo.AI/Agent
```

Для запуска и остановки агентом IDP-ядра без ввода пароля установите следующую настройку:
```
sudo sh -c "echo 'agent ALL=(%primo-ai) NOPASSWD: /app/Primo.AI/Agent/kill.sh, /app/Primo.AI/IDP/start_inference.sh, /app/Primo.AI/IDP/start_training.sh, /app/Primo.AI/IDP/start_evaluation.sh' > /etc/sudoers.d/agent"
```

Установите агент как службу и настройте автозапуск:
```
sudo cp /app/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```

В конфигурационном файле `appsettings.ProdLinux.json` укажите:
* Адрес Primo.AI.Api и его компонентов.
* **AgentId** — уникальный идентификатор агента в виде значения с типом данных GUID. Идентификатор агента можно задать самостоятельно, а затем передать администратору вместе с IP-адресом, чтобы он добавил его в профиль целевой машины, либо наоборот — сначала создать целевую машину в разделе **Настройки ➝ Целевые машины**, скопировать автоматически заданный GUID и указать его в этом параметре.
* **UserName** — логин учетной записи агента.
* **Password** — пароль от учетной записи агента.

```
 	"Api": {
    		"AgentId": "{91E221E8-8E13-4100-8BCB-84EA318C32DA}", // Уникальный идентификатор агента 
			
    		"UserName": "agent",
    		"Password": "Xxxxxxxxxxxx",

    		"AuthBaseUrl": "https://primo-ai-api-server:44392",
    		"ApiBaseUrl": "https://primo-ai-api-server:44392",
    		"InferenceBaseUrl": "https://primo-ai-api-server:44392",
    		"LogsBaseUrl": "https://primo-ai-api-server:44392",
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
sudo systemctl start Primo.AI.Agent
```

Проверьте статус службы:
```
sudo systemctl status Primo.AI.Agent
```

Просмотрите журнал службы:
```
sudo journalctl -u Primo.AI.Agent
```

### Настройка правила брандмауэра ufw

Для разрешения доступа к API агента выполните команду:
```
sudo ufw allow 5002/tcp
```

## Установка IDP


### Вариант установки A

Установка IDP при наличии в репозиториях apt целевой машины python3.10/3.11, выхода в интернет, а также GNU C Library (glibc) версии 2.33 и выше.

<details>

<summary>Вариант установки A</summary>

Разверните файлы IDP на целевой машине (файл `A-IDP.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
sudo mkdir -p /app/Primo.AI/IDP 
```
```
sudo unzip /srv/samba/shared/install/A-IDP.zip -d /app/Primo.AI/IDP
```
```
sudo chmod -R 777 /app/Primo.AI/IDP
```

Установите библиотеки python3, tesseract и другие пакеты:
```
sudo apt install software-properties-common -y
```
```
sudo add-apt-repository ppa:deadsnakes/ppa
```
```
sudo apt-get update | sudo apt install python3.11 python3.11-venv python3.11-dev libsm6 libxext6 build-essential libssl-dev libffi-dev ffmpeg -y
```

Создайте и активируйте виртуальную среду venv:
```
python3.11 -m venv /app/Primo.AI/IDP/venv
```
```
source /app/Primo.AI/IDP/venv/bin/activate
```

Установите пакеты python:
```
python -m ensurepip --upgrade
```

* Если для IDP-процесса будет использоваться CPU:
```
pip3 install -r /app/Primo.AI/IDP/prequisites_cpu.txt
```
```
pip3 install -r /app/Primo.AI/IDP/requirements_cpu.txt
```
* Если для IDP-процесса будет использоваться GPU:
```
pip3 install -r /app/Primo.AI/IDP/prequisites.txt	
```
```	
pip3 install -r /app/Primo.AI/IDP/requirements.txt
```

Произведите финальную раздачу прав IDP:
```
sudo chmod -R 771 /app/Primo.AI/IDP
```
```
sudo chown -R agent:primo-ai /app/Primo.AI/IDP
```


</details>



### Вариант установки B

<details>

<summary>Шаг 1: Установка pyenv c Python 3.11 и виртуальной средой </summary>

Создайте временный каталог `pyenv` и переместитесь туда: 
```
mkdir /tmp/pyenv
```
```
cd /tmp/pyenv 
```
Скопируйте во временный каталог файлы pyenv из комплекта поставки (файл `B-pyenv.zip` должен находиться в каталоге `/srv/samba/shared/install`): 
```
sudo unzip /srv/samba/shared/install/B-pyenv.zip .
```
```
sudo chmod -R 771 .
```

Запустите скрипт установки `pyenv-installer.sh`: 
```
sudo ./pyenv-installer.sh agent primo-ai  <custom_home_dir_location>
```

Сообщение *«WARNING: The Python tkinter extension was not compiled and GUI subsystem has been detected. Missing the Tk toolkit?»* можно проигнорировать.

Удалите установочные файлы: 
```
sudo rm  -r /tmp/pyenv
```


</details>


<details>

<summary>Шаг 2: Установка зависимостей IDP в виртуальную среду </summary>

Создайте папку с инсталляцией:
```
sudo mkdir /app/Primo.AI/IDP
```

Переместитесь в папку с инсталляцией
```
cd /app/Primo.AI/IDP
```

Распакуйте архив с IDP в каталог `/app/Primo.AI/IDP` (файл `B-IDP.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
sudo unzip /srv/samba/shared/install/B-IDP.zip 
```
```
sudo chmod -R 771 /app/Primo.AI/IDP
```

Запустите скрипт установки `idp-installer.sh`:
```
sudo ./idp-installer.sh agent primo-ai <custom_home_dir_location>
```

Раздайте права на IDP:
```
sudo chmod -R 771 /app/Primo.AI/IDP
```
```
sudo chown -R agent:primo-ai /app/Primo.AI/IDP
```
Удалите установочные файлы: 
```
sudo rm -r /app/Primo.AI/IDP/idp-installer.sh /app/Primo.AI/IDP/venv.zip 
```

</details>




### Вариант установки C

<details>

<summary>Вариант установки C</summary>

Создайте временную папку с инсталляцией:
```
sudo mkdir -p install/idp-deps
```
Распакуйте архивы с зависимостями:
```
yes | sudo unzip /srv/samba/shared/install/C-pkgs.zip -d install/idp-deps
```
Последовательно установите зависимости:
```
sudo dpkg -i install/idp-deps/python3.11/*.deb
```
```
sudo dpkg -i install/idp-deps/python3.11-venv/*.deb
```
```
sudo dpkg -i install/idp-deps/python3.11-dev/*.deb
```
```
sudo dpkg -i install/idp-deps/ffmpeg/*.deb
```

Проверьте, что python3.11 доступен для вызова:
```
which python3.11
```
> /usr/bin/python3.11 

Удалите временные файлы: 
```
sudo rm -r install/idp-deps
```

Создайте папку с инсталляцией:
```
sudo mkdir /app/Primo.AI/IDP
```

Перейдите в папку с инсталляцией:
```
cd /app/Primo.AI/IDP
```

Распакуйте архив с IDP в каталог `/app/Primo.AI/IDP` (файл `C-IDP.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
sudo unzip /srv/samba/shared/install/C-IDP.zip 
```

Создайте виртуальное окружение:
```
python -m venv /app/Primo.AI/IDP/venv 
```

Разместите в виртуальном окружении зависимости:
```
yes | sudo unzip /app/Primo.AI/IDP/venv.zip -d /app/Primo.AI/IDP/venv/
```

Удалите временные файлы: 
```
sudo rm /app/Primo.AI/IDP/venv.zip
```

Раздайте права на IDP:
```
sudo chmod -R 771 /app/Primo.AI/IDP
```
```
sudo chown -R agent:primo-ai /app/Primo.AI/IDP
```

</details>



### Установка Tesseract

<details>

<summary>При наличии менеджера пакетов apt</summary>


Проверьте наличие Tesseract версии 4.0.0+: 
```
sudo apt policy tesseract-ocr
tesseract-ocr: 
 Установлен:                   (отсутствует) 
 Кандидат:   4.0.0-2~bpo9+1
```

Установите Tesseract:
```
sudo apt install tesseract-ocr
```

</details>




<details>

<summary>В отсутствие менеджера пакетов apt</summary>


Создайте временную папку:
```
sudo mkdir -p install/idp-deps/tesseract-ocr
```
Распакуйте пакеты для Tesseract из варианта установки C: 
```
yes | sudo unzip /srv/share/C-pkgs.zip "tesseract-ocr/*" -d install/idp-deps/tesseract-ocr
```
Установите зависимости:
```
sudo dpkg -i install/idp-deps/tesseract-ocr/*.deb
```
Удалите временные файлы: 
```
sudo rm -r install/idp-deps/tesseract-ocr
```

</details>

### Проверка работоспособности

{% hint style="warning" %}
Переходите к этому шагу после установки Tesseract.
{% endhint %}


Создайте папку с тестовыми данными:
```
sudo mkdir -p install/idp-test
```
Распакуйте архивы с зависимостями:
```
yes | sudo unzip /srv/samba/shared/install/C-IDP-test.zip -d install/idp-test
```
Раздайте права:
```
sudo chown -R agent install/idp-test
```
```
sudo chmod -R 777 install/idp-test
```
Запустите IDP-процесс на тестовых данных:
```
/app/Primo.AI/IDP/start-inference.sh install/idp-test/Config/snils/1/config.json
```
Проверьте, что IDP-процесс сформировал корректные логи:
```
cat /app/Primo.AI/IDP/output.log
```

{% hint style="success" %}
Manager initialized successfully.
{% endhint %}

Теперь, когда IDP-модуль готов принимать изображения для распознавания, передайте ему тестовое изображение:
```
sudo cp install/idp-test/snils.jpg  install/idp-test/HotDir/snils/
```
Подождите немного, проверьте наличие файла с результатами:
```
cat install/idp-test/HotDir/snils/snils.jpg.result
```


## Увеличение лимита потребления ресурсов

При большой нагрузке на целевую машину происходит открытие множества дескрипторов файлов, что приводит к ошибке – "Too many open files". Необходимо увеличить системный лимит на количество дескрипторов, доступных пользователям. Для этого отредактируйте файл limits.conf:
```
sudo nano /etc/security/limits.conf
```

Добавьте туда следующие строки:
```
agent         hard    nofile      128000
agent         soft    nofile      128000
```

## Что дальше

[Выполните шаги](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/agent/post-installation-steps), необходимые после установки компонентов.
