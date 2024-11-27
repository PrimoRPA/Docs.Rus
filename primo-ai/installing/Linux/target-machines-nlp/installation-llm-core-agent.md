# Установка агента LLM-ядра

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                                     | Описание                     | Примечание                                                                    |
| ---------------------------------------- | ---------------------------- | ----------------------------------------------------------------------------- |
| `target-machines-nlp-llm-core-agent.7z`  | Дистрибутив агента LLM-ядра  | Содержит образ docker, docker-compose.yml и тома для подключения к контейнеру |


## Загрузка образа

```
docker load -i /srv/samba/shared/install/docker/target-machines-nlp-llm-core-agent/image.tar
```

## Создание контейнера

### 1. Размещение томов контейнера

Выполните команды:
```
sudo mkdir -p /app/Primo.AI/NLP/llm-core-agent/volumes/conf/Agent/ /app/Primo.AI/NLP/llm-core-agent/volumes/AgentData
```
```
cp /srv/samba/shared/install/docker/target-machines-nlp-llm-core-agent/docker-compose.yaml /app/Primo.AI/NLP/llm-core-agent
```
```
cp /srv/samba/shared/install/docker/target-machines-nlp-llm-core-agent/conf/Agent/* /app/Primo.AI/NLP/llm-core-agent/volumes/conf/Agent/
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/NLP/llm-core-agent
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
nano /app/Primo.AI/NLP/llm-core-agent/docker-compose.yaml
```
При необходимости можно указать, например, другой порт агента, имя контейнера, скорректировать пути к общим томам или отключить автоматический рестарт контейнера.

### 3. Файл конфигурации агента

Отредактируйте файл конфигурации агента Primo RPA AI Server:
```
nano /app/Primo.AI/NLP/llm-core-agent/volumes/conf/Agent/appsettings.ProdLinux.json
```

Обратите внимание на адрес **сервера** Primo RPA AI Server (ключи Api > AuthBaseUrl / ApiBaseUrl / InferenceBaseUrl / LogsBaseUrl).

### 4. Создание контейнера

```
cd /app/Primo.AI/NLP/llm-core-agent
```
```
docker compose up -d
```

## Что дальше
Выполните установку LLM-ядра на текущей машине.
* [LLM-ядро](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp/installation-llm-core-agent)
