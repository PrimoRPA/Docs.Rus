# Установка с использованием Docker

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                                         | Описание                                          |
| -------------------------------------------- | ------------------------------------------------- | 
| `docker/agents/SmartOCR/agent_ai.tar`        | Образ docker целевой машины с *Умным OCR*         | 
| `docker/agents/SmartOCR/docker-compose.yaml` | Файл с инструкциями по запуску контейнера         | 
| `docker/agents/SmartOCR/volumes/conf/`       | Файлы конфигурации для подключения к контейнеру   |          
| `docker/agents/SmartOCR/volumes/venv.zip`    | Архив с библиотеками для подключения к контейнеру |    


## Установка Docker

[Установите Docker](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/installing-docker).

## Создание контейнера

### Загрузка образа

```
docker load -i /srv/samba/shared/install/docker/agents/SmartOCR/agent_ai.tar
```

### 1. Размещение томов контейнера

Создайте папку /app/Primo.AI/SmartOCR и дочерние:
```
sudo mkdir -p /app/Primo.AI/SmartOCR/volumes/conf/Agent/ /app/Primo.AI/SmartOCR/volumes/IDP/lib/ /app/Primo.AI/SmartOCR/volumes/AgentData
```
Распакуйте архив с библиотеками в папку с томами контейнера:
```
yes | sudo unzip /srv/samba/shared/install/docker/agents/SmartOCR/volumes/venv.zip -d /app/Primo.AI/SmartOCR/volumes/IDP/lib
```
Скопируйте файл с инструкциями для запуска контейнера:
```
cp /srv/samba/shared/install/docker/agents/SmartOCR/docker-compose.yaml /app/Primo.AI/SmartOCR/
```
Скопируйте конфигурационные файлы Агента целевой машины:
```
cp /srv/samba/shared/install/docker/agents/SmartOCR/conf/Agent/* /app/Primo.AI/SmartOCR/volumes/conf/Agent/
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
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

### 2. Настройка docker-compose.yaml
Используйте команду:
```
nano /app/Primo.AI/SmartOCR/docker-compose.yaml
```
Настройте потребляемые контейнером ресурсы целевой машины:
```
    deploy:
      resources:
        limits:
          cpus: '4'
          memory: 16G
```
При необходимости можно указать, например, другой порт агента, имя контейнера, скорректировать пути к общим томам или отключить автоматический рестарт контейнера.

### 3. Файл конфигурации агента

Отредактируйте файл конфигурации агента Primo RPA AI Server:
```
nano /app/Primo.AI/SmartOCR/volumes/conf/Agent/appsettings.ProdLinux.json
```

Обратите внимание на идентификатор агента (ключ Api > AgentId). Он должен соответствовать идентификатору в настройках "Целевые машины" портала AI Server.

Также настройте адрес сервера Primo RPA AI Server (ключи Api > AuthBaseUrl / ApiBaseUrl / InferenceBaseUrl / LogsBaseUrl).

Также укажите ограничение на максимальное количество параллельно обрабатываемых запросов: параметр InferenceRequestQueue > MaxImagesLoad. 
Параметр рассчитывается по формуле 0.5n-1, где n - кол-во виртуальных ядер процессора (соответствует параметру deploy > resources limits > cpus файла конфигурации docker-compose.yaml).

### 4. Создание контейнера

```
cd /app/Primo.AI/SmartOCR/
```
```
docker compose up -d
```

## Что дальше
[Выполните шаги](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machine-smart-ocr/post-installation-steps), необходимые после установки компонентов.
