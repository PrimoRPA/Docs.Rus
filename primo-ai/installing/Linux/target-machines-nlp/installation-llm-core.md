# Установка LLM-ядра

## Установка Docker

[Установите Docker](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/installing-docker).

## Выбор устройства

LLM-модели отличаются высокой требовательностью к производительности. Время генерации токенов на графическом ускорителе на порядок выше, чем на ЦПУ.

## Выбор ядра

Primo RPA AI Server поддерживает 2 разновидности LLM-ядра - vLLM и Llama.cpp. 
Для высокопроизводительных вычислений на графической карте подходит vLLM, тогда как Llama.cpp лучше работает на CPU (отличается меньшим временем генерации первого токена). 
Llama.cpp на текущий момент не поддерживается для GPU.

Выбор ядра также влияет на выбор модели. Модель base-LLM-03 поддерживается только движком vLLM, тогда как модель base-LLM-01/base-LLM-02 – это версии одной модели для разных движков.

Для работы с LLM-ядром необходимо выбрать хотя бы 1 вариант из представленных. При выборе нескольких вариантов, повторите для каждого из них шаги 1-4 настоящей статьи.

## Установка LLM-ядра

### 1. Файлы из комплекта поставки

Скопируйте на целевую машину файлы в зависимости от выбранного движка, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                                                          | Описание                                         |
| ------------------------------------------------------------- | ------------------------------------------------ |
| `docker/agents/NLP/vllm/vllm-gpu.tar`                         | Дистрибутив LLM-ядра на движке vLLM для GPU      | 
| `docker/agents/NLP/vllm/vllm-cpu.tar`                         | Образ LLM-ядра на движке vLLM для CPU            | 
| `docker/agents/NLP/llama/llama_cpu_server.tar`                | Образ LLM-ядра на движке Llama.cpp для CPU       | 
| `docker/agents/NLP/llama/docker-compose-cpu.yml`              | Файл с инструкциями для запуска Llama.cpp на CPU | 

### 2. Загрузка образа

Для **vLLM для GPU**: 
```
docker load -i /srv/samba/shared/install/docker/agents/NLP/vllm/vllm-gpu.tar
```

Для **vLLM для CPU**: 
```
docker load -i /srv/samba/shared/install/docker/agents/NLP/vllm/vllm-cpu.tar
```

Для **Llama.cpp**: 
```
docker load -i /srv/samba/shared/install/docker/agents/NLP/llama/llama_cpu_server.tar
```

### 3. Создание рабочей папки 

```
sudo mkdir -p /app/Primo.AI/NLP/
```
```
sudo chown -R agent /app/Primo.AI/NLP
```

### 4. Размещение docker-compose 

Только для **Llama.cpp**.

Выполните команды:
```
sudo mkdir -p /app/Primo.AI/NLP/llm-core-llama-cpu/
```
```
cp /srv/samba/shared/install/docker/agents/NLP/llama/docker-compose-cpu.yml /app/Primo.AI/NLP/llm-core-llama-cpu/
```
```
sudo chown -R agent /app/Primo.AI/NLP
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/NLP/llm-core-llama-cpu
└── docker-compose-cpu.yml
```

