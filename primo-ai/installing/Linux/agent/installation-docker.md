# Установка компонентов целевой машины с использованием docker

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — их вы найдете в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл              | Описание                                 | Примечание                                                                                                         |
| ----------------- | ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------ |
| target-machine.7z | Дистрибутив целевой машины с "Умным OCR" | Содержит образ docker, docker-compose.yml и тома (с конфигурацией, данными целевой машины и библиотеками IDP-ядра) |


## Установка Docker

Настоящее краткое руководство основано на официальной инструкции - [Install Docker Engine from binaries](https://docs.docker.com/engine/install/binaries/).

### 1. При наличии интернета, загрузите свежий архив с официального сайта: 

Или воспользуйтесь предоставленной версией 27.3.1.

### 2. Распакуйте архив во временную папку: 
```
mkdir -p install/docker
```
```
cd install/docker
```
```
tar xzvf /srv/samba/shared/install/docker/install/docker/docker-27.3.1.tgz
```

### 3. Переместите распакованные компоненты Докера в /usr/bin/ 
```
sudo cp docker/* /usr/bin/
```

### 4. Установите зависимости:
```
mkdir -p install/iptables
```
```
yes | sudo unzip /srv/samba/shared/install/docker/install/iptables.zip -d install/iptables
```
```
sudo dpkg -i install/iptables/*.deb
```

### 5. Установите docker-compose:
```
sudo dpkg -i /srv/samba/shared/install/docker/install/docker/docker-compose-plugin_2.27.1-1~debian.10~buster_amd64.deb
```

### 6. Установите системную службу:
```
sudo cp /srv/samba/shared/install/docker/docker.service /etc/systemd/system/
```

```
sudo systemctl enable docker.service
```

```
sudo systemctl daemon-reload
```

```
sudo systemctl restart docker
```

## Загрузка образа
```
docker load -i /srv/samba/shared/install/docker/target-machine/agent_ai.tar
```

## Создание контейнера

### 1. Разместите тома контейнера:
```
sudo mkdir -p /app/Primo.AI/SmartOCR/volumes/conf/Agent/ /app/Primo.AI/SmartOCR/volumes/IDP/lib/ /app/Primo.AI/SmartOCR/volumes/AgentData
```
```
yes | sudo unzip /srv/samba/shared/install/docker/target-machine/python3.11.zip -d /app/Primo.AI/SmartOCR/volumes/IDP/lib
```
```
cp /srv/samba/shared/install/docker/target-machine/docker-compose.yaml /app/Primo.AI/SmartOCR/
```
```
cp /srv/samba/shared/install/docker/target-machine/conf/Agent/* /app/Primo.AI/SmartOCR/volumes/conf/Agent/
```

Должна получиться такая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/SmartOCR/
├── docker-compose.yaml
└── volumes
    ├── AgentData
    ├── conf
    │   └── Agent
    │       ├── appsettings.json
    │       └── appsettings.ProdLinux.json
    └── IDP
        └── lib
            └── python3.11
                └── site-packages
```

### 2. Настройте docker-compose.yaml:
```
nano /app/Primo.AI/SmartOCR/docker-compose.yaml
```

### 3. Отредактируйте файл конфигурации агента Primo RPA AI Server:
```
nano /app/Primo.AI/SmartOCR/volumes/conf/Agent/appsettings.ProdLinux.json
```

Обратите внимание на идентификатор агента (ключ Api > AgentId). 
Он должен соответствовать идентификатору в настройках "Целевые машины" портала AI Server.

Также настройте адрес сервера Primo RPA AI Server (ключи Api > AuthBaseUrl / ApiBaseUrl / InferenceBaseUrl / LogsBaseUrl).

### 4. Создайте контейнер:
```
cd /app/Primo.AI/SmartOCR/
```
```
docker compose up -d
```