# Установка Logics-сервера

## Установка Docker

[Установите Docker](https://docs.primo-rpa.ru/primo-rpa/primo-ai-server/installing/linux/installing-docker).

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                            | Описание                   | Примечание                                                                    |
| ------------------------------- | -------------------------- | ----------------------------------------------------------------------------- |
| `target-machines-nlp-logics.7z` | Дистрибутив Logics-сервера | Содержит образ docker, docker-compose.yml и тома для подключения к контейнеру |

## Загрузка образа

```
docker load -i /srv/samba/shared/install/docker/target-machines-nlp-logics/image.tar
```

## Создание контейнера

### 1. Размещение томов контейнера

Выполните команды:
```
sudo mkdir -p /app/Primo.AI/NLP/logics/volumes/src/ /app/Primo.AI/NLP/logics/volumes/venv
```
```
sudo cp /srv/samba/shared/install/docker/target-machines-nlp-logics/docker-compose.yaml /app/Primo.AI/NLP/logics/
```
```
sudo cp /srv/samba/shared/install/docker/target-machines-nlp-logics/conf/src/* /app/Primo.AI/NLP/logics/volumes/src/
```
```
sudo cp /srv/samba/shared/install/docker/target-machines-nlp-logics/conf/venv.zip /app/Primo.AI/NLP/logics/volumes/venv/
```
```
sudo unzip /app/Primo.AI/NLP/logics/volumes/venv/venv.zip
```
```
sudo rm -r /app/Primo.AI/NLP/logics/volumes/venv/venv.zip
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/NLP/logics/
├── docker-compose.yaml
└── volumes
    ├── src
    ├── venv
    │   └── lib
    │       └── python3.11
```

### 2. Настройка docker-compose.yaml
Используйте команду:
```
nano /app/Primo.AI/NLP/logics/docker-compose.yaml
```
При необходимости можно указать, например, другой порт агента, имя контейнера, скорректировать пути к общим томам или отключить автоматический рестарт контейнера.

## Что дальше
Выполните установку агента LLM-ядра на текущей или иной машине.
* [LLM-ядро](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp/installation-llm-core-agent)
