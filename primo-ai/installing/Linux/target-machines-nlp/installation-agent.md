# Установка агента 

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                           | Описание           | Примечание                                                                    |
| ------------------------------ | ------------------ | ----------------------------------------------------------------------------- |
| `target-machines-nlp-agent.7z` | Дистрибутив агента | Содержит образ docker, docker-compose.yml и тома для подключения к контейнеру |

## Загрузка образа

```
docker load -i /srv/samba/shared/install/docker/target-machines-nlp-agent/image.tar
```

## Создание контейнера

### 1. Размещение томов контейнера

Выполните команды:
```
sudo mkdir -p /app/Primo.AI/NLP/agent/volumes/conf/Agent/ /app/Primo.AI/NLP/agent/volumes/AgentData
```
```
cp /srv/samba/shared/install/docker/target-machines-nlp-agent/docker-compose.yaml /app/Primo.AI/NLP/agent/
```
```
cp /srv/samba/shared/install/docker/target-machines-nlp-agent/conf/Agent/* /app/Primo.AI/NLP/agent/volumes/conf/Agent/
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/NLP/agent/
├── docker-compose.yaml
└── volumes
    ├── AgentData
    ├── conf
    │   └── Agent
    │       ├── appsettings.json
    │       └── appsettings.ProdLinux.json
```

### 2. Настройка docker-compose.yaml
Используйте команду:
```
nano /app/Primo.AI/NLP/agent/docker-compose.yaml
```
При необходимости можно указать, например, другой порт агента, имя контейнера, скорректировать пути к общим томам или отключить автоматический рестарт контейнера.

### 3. Файл конфигурации агента

Отредактируйте файл конфигурации агента Primo RPA AI Server:
```
nano /app/Primo.AI/NLP/agent/volumes/conf/Agent/appsettings.ProdLinux.json
```

Обратите внимание на **идентификатор агента** (ключ Api > AgentId). Он должен соответствовать идентификатору в настройках "Целевые машины" портала AI Server.

Также настройте адрес **сервера** Primo RPA AI Server (ключи Api > AuthBaseUrl / ApiBaseUrl / InferenceBaseUrl / LogsBaseUrl), адрес **агента LLM-ядра** (ключ Api > NlpEngineAgentBaseUrl) и адрес **Logics-сервера** (ключ Api > LogicsServerBaseUrl).

### 4. Создание контейнера

```
cd /app/Primo.AI/NLP/agent
```
```
docker compose up -d
```

## Что дальше
Выполните установку Logics-сервера на машине с агентом.
* [Logics-сервер](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp/installation-logics-server)
