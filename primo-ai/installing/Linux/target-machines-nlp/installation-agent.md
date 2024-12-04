# Установка агента 

## Файлы из комплекта поставки

Скопируйте на целевую машину файлы, приведенные в таблице ниже — они находятся в комплекте поставки Primo RPA AI Server. Остальное ПО должно быть предустановлено в Astra Linux.

| Файл                    | Описание           |
| ----------------------- | ------------------ |
| `distr/Agent-linux.zip` | Дистрибутив агента |


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

    		"AuthBaseUrl": "https://primo-ai-api-server:44392",
    		"ApiBaseUrl": "https://primo-ai-api-server:44392",
    		"InferenceBaseUrl": "https://primo-ai-api-server:44392",
    		"LogsBaseUrl": "https://primo-ai-api-server:44392",
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
