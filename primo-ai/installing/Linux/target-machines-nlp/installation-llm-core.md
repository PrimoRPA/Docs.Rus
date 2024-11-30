# Установка LLM-ядра

## Выбор устройства

TODO

LLM-модели отличаются высокой требовательностью к производительности. Время генерации токенов на графическом ускорителе на порядок выше, чем на ЦПУ.

## Выбор ядра

TODO

Primo RPA AI Server поддерживает 2 разновидности LLM-ядра - vLLM и Llama. 
Для высокопроизводительных вычислений на графической карте подходит vLLM, тогда как Llama лучше работает на CPU (отличается меньшим временем генерации первого токена). 
Llama на текущий момент не поддерживается для GPU.

Для работы с LLM-ядром необходимо выбрать хотя бы 1 вариант из представленных. При выборе нескольких вариантов, повторите для каждого из них шаги 1-4 настоящей статьи.

## Установка LLM-ядра

### 1. Файлы из комплекта поставки

Скопируйте на целевую машину файлы в зависимости от выбранного движка, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                                        | Описание                                     | Примечание                                    |
| ------------------------------------------- | -------------------------------------------- |-----------------------------------------------|
| `target-machines-nlp-llm-core-vllm-gpu.7z`  | Дистрибутив LLM-ядра на движке vLLM для GPU  | Содержит образ docker                         |
| `target-machines-nlp-llm-core-vllm-cpu.7z`  | Дистрибутив LLM-ядра на движке vLLM для CPU  | Содержит образ docker                         |
| `target-machines-nlp-llm-core-llama-cpu.7z` | Дистрибутив LLM-ядра на движке Llama для CPU | Содержит образ docker, docker-compose-cpu.yml |

### 2. Загрузка образа

Для **vLLM для GPU**: 
```
docker load -i /srv/samba/shared/install/docker/target-machines-nlp-llm-core-vllm-gpu/image.tar
```

Для **vLLM для CPU**: 
```
docker load -i /srv/samba/shared/install/docker/target-machines-nlp-llm-core-vllm-cpu/image.tar
```

Для **Llama**: 
```
docker load -i /srv/samba/shared/install/docker/target-machines-nlp-llm-core-llama-cpu/image.tar
```

### 3. Размещение docker-compose 

Только для **Llama**.

Выполните команды:
```
sudo mkdir -p /app/Primo.AI/NLP/llm-core-llama-cpu/
```
```
cp /srv/samba/shared/install/docker/target-machines-nlp-llm-core-llama-cpu/docker-compose-cpu.yml /app/Primo.AI/NLP/llm-core-llama-cpu/
```

Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
```
/app/Primo.AI/NLP/llm-core-llama-cpu
├── docker-compose-cpu.yml
```

## Что дальше
Выполните установку Logics-сервера на машине с агентом.
* [Logics-сервер](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp-llm-core-agent/installation-logics-server)
