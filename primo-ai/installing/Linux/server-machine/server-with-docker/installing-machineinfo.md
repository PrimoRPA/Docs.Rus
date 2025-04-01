# Установка Primo.AI.Api.MachineInfo 

## Размещаем файлы компонента
1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.MachineInfo`:
   ```
   sudo mkdir -p /app/Primo.AI/Api.MachineInfo
   ```
1. Разархивируем `Api.MachineInfo-linux.zip` в `/app/Primo.AI/Api.MachineInfo`:
   ``` 
   sudo unzip /srv/samba/shared/install/distr/Api.MachineInfo-linux.zip -d /app/Primo.AI/Api.MachineInfo
   ```
1. Устанавливаем владельца папки с инсталляцией:
   ```
   sudo chown -R primo:primo-ai /app/Primo.AI/Api.MachineInfo
   ```

## Создаем и настраиваем службу
	 
1. Копируем файл службы из комплекта поставки в `/etc/systemd/system`:
   ```
   sudo cp /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo.service /etc/systemd/system/Primo.AI.Api.MachineInfo.service
   ```
1. Перезагружаем systemctl:
   ```
   sudo systemctl daemon-reload	
   ```
1. Помещаем службу в автозапуск:
   ```
   sudo systemctl enable /etc/systemd/system/Primo.AI.Api.MachineInfo.service
   ```
	
## Даем права на запуск

1. Назначаем права:
   ```
   sudo chmod -R 770 /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo
   ```
1. Проверяем выполнение команды:
   ```
   sudo lsblk --nodeps -no serial /dev/sda
   ```

   Если команда выполнится с ошибкой, находим вместо `/dev/sda` другое блочное устройство (диск) и прописываем его в конфигурационном файле:
 
   ![](<../../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-devices.png>)


## Настройка службы
Открываем порт:
```
sudo ufw allow 5051/tcp
```

## Вспомогательные компоненты
Устанавливаем пакет cpuid:
```
sudo unzip /srv/samba/shared/install/distr/cpuid.zip -d /srv/samba/shared/install/distr/cpuid
```
```
sudo dpkg -i /srv/samba/shared/install/distr/cpuid/*.deb
```

## Настройка Primo RPA AI Server для работы с MachineInfo

{% hint style="info" %} Вернитесь к этому пункту после настройки остальных компонентов Api. {% endhint %}

Открываем на редактирование файл конфигурации Primo.AI.Api:
```
sudo nano /app/Primo.AI/Api/volumes/conf/Api/appsettings.ProdLinux.json
```

1. Если используется один сервер с MachineInfo, прописываем ссылку на него:

   ![](<../../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-4.png>)
 
   Параметр **Timeout** – время ответа, после которого сервис считается недоступным. По умолчанию равен 4 сек.

2. Если используется кластер MachineInfo, или MachineInfo используется в геокластере, то прописываем ссылки на все узлы кластера:

   ![](<../../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-5.png>)

   Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. 

   Узлы нельзя скрывать за балансировщиком нагрузки (load balancer).

{% hint style="info" %} Указанные выше URL должны быть доступны изнутри контейнера server_api. Например, для bridge-сети (конфигурация сети задается в docker-compose-файле сервера) адрес хоста – 172.17.0.1. {% endhint %}

После перенастройки Primo.AI.Api, перезапустите контейнер server_api:
```
docker restart server_api
```

## Запускаем службу

1. Запускаем службу:
   ```
   sudo systemctl start Primo.AI.Api.MachineInfo
   ```
1. Проверяем состояние службы:
   ```
   sudo systemctl status Primo.AI.Api.MachineInfo
   ```

## Что дальше

[Установите Api и его компоненты](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/installing/linux/server-machine/server-with-docker/installing-api).
