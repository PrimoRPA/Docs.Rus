# Установка агента LLM-ядра

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                               | Описание                     | 
| ---------------------------------- | ---------------------------- |
| `distr/Agent.NlpEngine-linux.zip`  | Дистрибутив агента LLM-ядра  |

## Подготовка к установке

При установке Astra Linux на целевой машине необходимо создать пользователя-администратора. Для этого на экране «Настройка учетных записей и паролей» введите имя `primo-admin` для учетной записи администратора.

![Настройка учетных записей и паролей](<../../../../.gitbook/assets1/primo-ai/install/create-admin-user.png>)

Установка дополнительного ПО и создание дополнительных пользователей описаны ниже.

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

Разверните файлы агента на целевой машине (файл `Agent.NlpEngine-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`): 
```
sudo mkdir -p /app/Primo.AI /app/Primo.AI/Agent.NlpEngine /app/Primo.AI/Agent.NlpEngineData 
```
```
sudo unzip /srv/samba/shared/install/Agent.NlpEngine-linux.zip -d /app/Primo.AI/Agent.NlpEngine
```
```
sudo chmod -R 771 /app/Primo.AI/Agent.NlpEngine /app/Primo.AI/Agent.NlpEngineData
```
```
sudo chown -R agent:primo-ai /app/Primo.AI/Agent.NlpEngine /app/Primo.AI/Agent.NlpEngineData /app/Primo.AI/Agent.NlpEngine
```

Установите агент как службу и настройте автозапуск:
```
sudo cp /app/Primo.AI/Agent/Primo.AI.Agent.NlpEngine.service /etc/systemd/system/
```
```
sudo systemctl daemon-reload
```
```
sudo systemctl enable /etc/systemd/system/Primo.AI.Agent.NlpEngine.service
```

В конфигурационном файле `appsettings.ProdLinux.json` укажите:
* **UserName** — логин учетной записи агента.
* **Password** — пароль от учетной записи агента.
* Адрес Primo.AI.Api и его компонентов.

```
 	"Api": {
    		"UserName": "agent",
    		"Password": "Xxxxxxxxxxxx",

    		"AuthBaseUrl": "https://primo-ai-api-server:44392",
    		"ApiBaseUrl": "https://primo-ai-api-server:44392",
    		"InferenceBaseUrl": "https://primo-ai-api-server:44392",
    		"LogsBaseUrl": "https://primo-ai-api-server:44392",
  },
```

Запустите службы:
```
sudo systemctl start Primo.AI.Agent.NlpEngine
```

Проверьте статус службы:
```
sudo systemctl status Primo.AI.Agent.NlpEngine
```

Просмотрите журнал службы:
```
sudo journalctl -u Primo.AI.Agent.NlpEngine
```

### Настройка правила брандмауэра ufw

Для разрешения доступа к API агента выполните команду:
```
sudo ufw allow 5005/tcp
```


## Что дальше
Выполните установку LLM-ядра на текущей машине.
* [LLM-ядро](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/target-machines-nlp/installation-llm-core-agent)
