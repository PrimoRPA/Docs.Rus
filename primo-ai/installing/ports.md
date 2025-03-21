# Сетевые порты

Ниже представлен список сетевых портов, которые используются при настройке конфигурационных файлов компонентов Primo RPA AI Server, целевых машин и открытия портов на файерволе.

| Порт  | Протокол  | HTTPS  | Назначение                                                         | 
| ----- | --------- | ------ | ------------------------------------------------------------------ |
| 44392 | TCP       | Да     | Порт для подключения к Primo.AI.Api (и его компонентам) через реверс-прокси Nginx, а также к UI |
| 5556  | TCP       | Нет    | Порт для подключения к Primo.AI.Api напрямую                       |
| 5555  | TCP       | Нет    | Порт для подключения к Primo.AI.Api.Auth напрямую                  |
| 5078  | TCP       | Нет    | Порт для подключения к Primo.AI.Api.Logs напрямую                  |
| 5012  | TCP       | Нет    | Порт для подключения к Primo.AI.Api.Inference напрямую             |
| 5051  | TCP       | Да     | Порт для подключения к Primo.AI.Api.MachineInfo                    |
| 5432  | TCP       | Нет    | Порт для подключения к серверу БД PostgresSQL                      |
| 5672  | TCP       | Нет    | Порт для подключения к RabbitMQ                                    |
| 9001  | TCP       | Нет    | Порт для опционального подключения MinIO                           |
| 6379  | TCP       | Нет    | Порт для опционального подключения Redis                           |
| 5002  | TCP       | Да     | Порт для подключения к приложению Agent на целевой машине. <p>Агент служит для управления data science-ядром на целевой машине Умного OCR и Logics-сервером на целевой машине NLP </p> |
| 5005  | TCP       | Да     | Порт для подключения Agent.NlpEngine, который управляет LLM-ядром (компонент NLP) |
| 8001  | TCP       | Нет    | Порт для подключения Logics-сервера (компонент NLP)  |
| 8000  | TCP       | Нет    | Порт для подключения Vllm-ядра (компонент NLP)       |
| 8003  | TCP       | Нет    | Порт для подключения Llama-ядра (компонент NLP)      |
