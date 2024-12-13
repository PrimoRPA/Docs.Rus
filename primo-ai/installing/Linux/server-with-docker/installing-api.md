# Установка сервера AI

Подключаемся к серверу по SSH с пользователем с правами root. 

## Установка Docker

[Установите Docker](https://docs.primo-rpa.ru/primo-rpa/primo-ai-server/installing/linux/installing-docker).

## Создаем подсеть сервера

```
docker network create --driver=bridge --subnet=192.168.0.0/16 server_ai
```

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
```
docker load -i /srv/samba/shared/install/docker/server/postgres.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/rabbitmq.tar
```
```
docker load -i /srv/samba/shared/install/docker/server/portainer.tar
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
   sudo cp /srv/samba/shared/install/docker/server/.env /app/Primo.AI/Api/
   ```
   ```
   sudo cp -r /srv/samba/shared/install/docker/server/volumes/* /app/Primo.AI/Api/volumes/
   ```
1. Размещаем файлы моделей "Умного OCR": 
   ```
   sudo cp -r /srv/samba/shared/install/data/models/SmartOCR/* /app/Primo.AI/Api/volumes/Api_Models/
   ```
1. Размещаем файлы моделей "AI Текст". Файлы моделей объемные, поэтому можно скопировать только отдельные.

   Базовая модель 'Llama' для vLLM-ядра:
   ```
   sudo cp -r /srv/samba/shared/install/data/models/NLP/llama3.1-8B.zip /app/Primo.AI/Api/volumes/Api_Models/
   ```
   Базовая модель 'Llama' для Llama-ядра:
   ```
   sudo cp -r /srv/samba/shared/install/data/models/NLP/llama3.1-8B-GGUF.zip /app/Primo.AI/Api/volumes/Api_Models/
   ```
   Базовая модель 'Qwen' для vLLM-ядра:
   ```
   sudo cp -r /srv/samba/shared/install/data/models/NLP/qwen2.5-7B.zip /app/Primo.AI/Api/volumes/Api_Models/
   ```
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
       │   ├─── model-1.zip
       │   ├─── model-2.zip
       │   ├─── model-3.zip
       │   └─── model-N.zip
       ├── Api_ContextFiles
       │   ├─── classification-ctx.json
       │   ├─── extraction-ctx.json
       │   ├─── generation-ctx.json
       │   └─── summarization-ctx.json
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
   
   

   
## Создание контейнера

   ```
   cd /app/Primo.AI/Api/
   ```
   ```
   docker compose up -d
   ```
