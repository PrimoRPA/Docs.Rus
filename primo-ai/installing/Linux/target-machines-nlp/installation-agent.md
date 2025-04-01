# Установка агента 

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                    | Описание           |
| ----------------------- | ------------------ |
| `distr/Agent-linux.zip` | Дистрибутив агента |

## Установка агента

### Настройка учетной записи 

Для работы агента создайте группу **primo-ai** и учетную запись **agent**. 
```
sudo groupadd primo-ai
```

```
sudo useradd -g primo-ai -m -s /bin/bash agent
```

### Установка агента

Разверните файлы агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`): 
```
sudo mkdir -p /app/Primo.AI /app/Primo.AI/Agent /app/Primo.AI/AgentData 
```
```
sudo unzip /srv/samba/shared/install/Agent-linux.zip -d /app/Primo.AI/Agent
```
```
sudo chmod -R 771 /app/Primo.AI/Agent /app/Primo.AI/AgentData
```
```
sudo chown -R agent:primo-ai /app/Primo.AI/Agent /app/Primo.AI/AgentData /app/Primo.AI/Agent
```

Установите агент как службу и настройте автозапуск:
```
sudo cp /app/Primo.AI/Agent/Primo.AI.Agent.service /etc/systemd/system/
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.service
```

В конфигурационном файле `appsettings.ProdLinux.json` укажите:
* **AgentId** — уникальный идентификатор агента в виде значения с типом данных GUID. Идентификатор агента можно задать самостоятельно, а затем передать администратору вместе с IP-адресом, чтобы он добавил его в профиль целевой машины, либо наоборот — сначала создать целевую машину в разделе **Настройки ➝ Целевые машины**, скопировать автоматически заданный GUID и указать его в этом параметре.
* **UserName** — логин учетной записи агента.
* **Password** — пароль от учетной записи агента.
* Адрес Primo.AI.Api и его компонентов.

```
 "Api": {
	"AgentId": "{91E221E8-8E13-4100-8BCB-84EA318C32DA}", // Уникальный идентификатор агента 
	
	"UserName": "agent",
	"Password": "Xxxxxxxxxxxx", 
	
	"AuthBaseUrl": "https://primo-rpa-ai-server:44392",
	"ApiBaseUrl": "https://primo-rpa-ai-server:44392",
	"InferenceBaseUrl": "https://primo-rpa-ai-server:44392",
	"LogsBaseUrl": "https://primo-rpa-ai-server:44392",
	
	"LogicsServerBaseUrl": "http://localhost:8001", // Реквизиты logics-сервера (расположен на 1-й машине с агентом)
	"NlpEngineAgentBaseUrl": "https://localhost:5005", // Реквизиты агента LLM-ядра (может быть на отдельной машине)
	
	"TenantId": null // Если агент обслуживает отдельный тенант, укажите его здесь
  },
```

Укажите параметры запуска logics-сервера в ключе NlpProcess: 
```
 "NlpProcess": {
    "HealthCheck": {
      "TimeoutSeconds": 120, // Как долго ждать полного запуска logics-сервера
      "PeriodMilliseconds": 500
    },
    "Engines": {
      "Vllm": {
        "Host": "vllm", // Находится в единой подсети с logics-сервером, поэтому доступен по имени контейнера
        "Port": 8000
      },
      "Llama": {
        "Host": "llama", // Находится в единой подсети с logics-сервером, поэтому доступен по имени контейнера
        "Port": 8003
      }
    },
    "LogicsDockerCompose": {
      "DockerComposeCommand": "docker compose", // Или docker-compose
      "DockerComposeYamlDirectory": "/app/Primo.AI/NLP/logics",
      "DockerComposeYamlFileName": "docker-compose.yml",
      "ConfigFileRelativePaths": [ "volumes/config/.env", ".env" ],
      "Host": "0.0.0.0",
      "Port": 8001, // Совпадает с портом в Api > LogicsServerBaseUrl
      "ImageName": "logics",
      "ContainerName": "logics"
    }
  },
```

Запустите службы:
```
sudo systemctl start Primo.AI.Agent
```

Проверьте статус службы:
```
sudo systemctl status Primo.AI.Agent
```

Просмотрите журнал службы:
```
sudo journalctl -u Primo.AI.Agent
```

### Настройка правила брандмауэра ufw

Для разрешения доступа к API агента выполните команду:
```
sudo ufw allow 5002/tcp
```

## Что дальше
Выполните установку Logics-сервера на машине с агентом.
* [Logics-сервер](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp/installation-logics-server)
