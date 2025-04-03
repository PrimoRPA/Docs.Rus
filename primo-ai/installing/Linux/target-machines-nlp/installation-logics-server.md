# Установка Logics-сервера

## Установка Docker

[Установите Docker](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/installing-docker)

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                                          | Описание                                                            | 
| --------------------------------------------- | ------------------------------------------------------------------- | 
| `docker/agents/NLP/logics/logics.tar`         | Дистрибутив Logics-сервера                                          |
| `docker/agents/NLP/logics/docker-compose.yml` | Файл с инструкциями для запуска docker-контейнера с Logics-сервером |
| `docker/agents/NLP/logics/volumes/venv.zip`   | Библиотеки необходимые Logics-серверу для работы                    |

## Загрузка образа

```
docker load -i /srv/samba/shared/install/docker/agents/NLP/logics/logics.tar
```

## Создание контейнера

### 1. Размещение томов контейнера

Выполните команды:
```
sudo mkdir -p /app/Primo.AI/NLP/logics/volumes/src/ /app/Primo.AI/NLP/logics/volumes/venv
```
```
sudo cp /srv/samba/shared/install/docker/agents/NLP/logics/docker-compose.yml /app/Primo.AI/NLP/logics/
```
```
sudo cp /srv/samba/shared/install/docker/agents/NLP/logics/volumes/venv.zip /app/Primo.AI/NLP/logics/volumes/venv/
```
```
sudo unzip /app/Primo.AI/NLP/logics/volumes/venv/venv.zip
```
```
sudo rm -r /app/Primo.AI/NLP/logics/volumes/venv/venv.zip
```
```
sudo chown -R agent /app/Primo.AI/NLP
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/NLP/logics/
├── docker-compose.yaml
└── volumes
    └── venv
        └── lib
            └── python3.11
```

### 2. Настройка docker-compose.yaml
Используйте команду:
```
nano /app/Primo.AI/NLP/logics/docker-compose.yml
```
При необходимости можно указать, например, другой порт агента, имя контейнера, скорректировать пути к общим томам или отключить автоматический рестарт контейнера.
Обратите внимание, что при запуске контейнера будет создана подсеть agent_ai, которая переиспользуется LLM-ядром. 

## Что дальше
Выполните установку агента LLM-ядра на текущей или иной машине.
* [Агент LLM-ядра](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp/installation-llm-core-agent)
