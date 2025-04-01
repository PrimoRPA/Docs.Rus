# Установка сервера AI

Подключаемся к серверу по SSH с пользователем с правами root. 

## Установка Docker

[Установите Docker](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/installing-docker).

{% hint style="warning" %}
**Примечание**. Сервер использует подсеть server_ai, которая создается автоматически при первом запуске финальной команды данной статьи.
{% endhint %}

## Загрузка образов

```
docker load -i /srv/samba/shared/install/docker/server/server_api.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/server_auth.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/server_inference.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/server_logs.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/server_ui.tar
```

При необходимости для сред разработки/тестирования загрузите сторонние зависимости:
```
docker load -i /srv/samba/shared/install/docker/server/postgres.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/rabbitmq.tar
```

## Размещение файлов

1. Создаем папку `/app/Primo.AI/Api` и дочерние:
   ```
   sudo mkdir -p /app/Primo.AI/Api/volumes/conf/Api/ /app/Primo.AI/Api/volumes/conf/Auth/ /app/Primo.AI/Api/volumes/conf/Logs/ /app/Primo.AI/Api/volumes/conf/MachineInfo/ /app/Primo.AI/Api/volumes/conf/Inference/ /app/Primo.AI/Api/volumes/nginx/ /app/Primo.AI/Api/volumes/Api_Models/ /app/Primo.AI/Api/volumes/Api_ContextFiles/ /app/Primo.AI/Api/volumes/Logs/ 
   ```
1. Размещаем окружение сервера в `/app/Primo.AI/Api`:
   ```
   sudo cp /srv/samba/shared/install/docker/server/docker-compose.yaml /app/Primo.AI/Api/
   ```
   ```
   sudo cp -r /srv/samba/shared/install/docker/server/volumes/* /app/Primo.AI/Api/volumes/
   ```
   ```
   sudo unzip /srv/samba/shared/install/docker/server/env.zip -d /app/Primo.AI/Api/
   ```
   Укажите пароль к БД, RabbitMQ, временную зону в .env-файле:
   ```
   sudo nano /app/Primo.AI/Api/.env
   ```
1. Размещаем файлы моделей "Умного OCR": 
   ```
   sudo cp -r /srv/samba/shared/install/data/models/SmartOCR/* /app/Primo.AI/Api/volumes/Api_Models/
   ```
1. Размещаем файлы моделей "AI Текст". 

  **Модели "AI Текст"**:
| Имя модели      | Тип LLM-ядра | Мультимодальность | Имя файла                            |
| --------------- |------------- | ----------------- | ------------------------------------ |
| base-LLM-01.zip | vLLM         | Нет               | e255188e-d9f6-41d3-b170-0c25bc0bd02f |	
| base-LLM-02.zip | Llama.cpp    | Нет               | ddc02d8d-0117-4c67-acb3-2dd0549d2985 |
| base-LLM-03.zip | vLLM         | Нет               | b1bf77a1-ca4e-4088-942c-8ec83086611b |
| base-LLM-04.zip | vLLM         | Да                | ebe98258-1c21-4d19-af56-cf39f7e3883d |

   Файлы моделей объемные, поэтому можно скопировать только отдельные (укажите вместо 'xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx' имя файла модели, воспользовавшись столбцом "Имя файла" из таблицы выше).
   ```
   sudo cp /srv/samba/shared/install/data/models/NLP/xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /app/Primo.AI/Api/volumes/Api_Models/
   ```
   Если разместить только часть моделей, при попытке использования остальных интерфейс системы будет выдавать ошибку.

1. Размещаем стандартный контекст NLP-запросов: 
   ```
   sudo cp -r /srv/samba/shared/install/data/context/* /app/Primo.AI/Api/volumes/Api_ContextFiles/
   ```
   Должна получиться следующая иерархия папок для соответствия стандартному docker-compose.yaml:
   ```
   /app/Primo.AI/Api/
   ├── .env
   ├── docker-compose.yaml
   └── volumes
       ├── conf
       │   └── Api
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── Logs
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── Inference
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── Auth
       │       ├── appsettings.json
       │       └── appsettings.ProdLinux.json
       │   └── nginx
       │       └── nginx.conf
       ├── Api_Models
       │   ├─── cf7d9f7f-ab96-4c15-873e-82c6aad7f9a4
       │   ├─── 3901af0a-8c50-4b76-b96f-481cae5e4a35
       │   ├─── ...
       │   └─── e255188e-d9f6-41d3-b170-0c25bc0bd02f
       ├── Api_ContextFiles
       │   ├─── 13fb0ff5-3f31-44e1-9c99-e24276380a3f
       │   ├─── e41cc59b-059f-4471-8d09-328aab8ed60f
       │   ├─── a9d109d6-0125-42f9-b44e-2052a0c4e164
       │   └─── d24b857c-6c21-4d5f-990f-52d6235c33dd
       └── Logs
   ```
## Редактируем конфигурационные файлы

### Редактируем конфигурационный файл Api

1. Открываем в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Api/appsettings.ProdLinux.json
   ```
1. Указываем адрес Портала AI Сервера в Security > EnabledOrigins:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392", 
      "https://ai-server-portal:44392"
    ],	
    ...
   }
   ```
   
### Редактируем конфигурационный файл Api.Auth

1. Открываем в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Auth/appsettings.ProdLinux.json
   ```
1. Указываем адрес Портала AI Сервера в Security > EnabledOrigins:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392", 
      "https://ai-server-portal:44392"
    ],	
    ...
   }
   ```   

### Редактируем конфигурационный файл Api.Inference

1. Открываем в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Inference/appsettings.ProdLinux.json
   ```
   
1. Указываем адрес Портала AI Сервера в Security > EnabledOrigins:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392", 
      "https://ai-server-portal:44392"
    ],	
    ...
   }
   ```
   
### Редактируем конфигурационный файл Api.Logs

1. Открываем в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/conf/Logs/appsettings.ProdLinux.json
   ```
1. Указываем адрес Портала AI Сервера в Security > EnabledOrigins:
   ```
   "Security": {
    ...
    "EnabledOrigins": [
      "https://192.168.0.4:44392", 
      "https://ai-server-portal:44392"
    ],	
    ...
   }
   ```
   
### Редактируем конфигурационный файл nginx

При необходимости можно указать в конфигурационном файле число рабочих процессов, максимальное число соединений, которые одновременно может открыть рабочий процесс и другие параметры.

1. Открываем в редакторе конфигурационный файл:
   ```
   sudo nano /app/Primo.AI/Api/volumes/nginx/nginx.conf
   ```
   
## Запуск контейнеров

   ```
   cd /app/Primo.AI/Api/
   ```
   ```
   docker compose up -d
   ```
