# Установка Primo.AI.Api.MachineInfo 

## Размещаем файлы компонента
1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.MachineInfo`:
   ```
   # sudo mkdir /app/Primo.AI/Api.MachineInfo
   ```
1. Разархивируем `Api.MachineInfo-linux.zip` в `/app/Primo.AI/Api.MachineInfo`:
   ``` 
   # sudo unzip /srv/samba/shared/install/Api.MachineInfo-linux.zip -d /app/Primo.AI/Api.MachineInfo
   ```
1. Устанавливаем владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api
   ```

## Создаем и настраиваем службу
	 
1. Копируем файл службы из комплекта поставки в `/etc/systemd/system`:
   ```
   # sudo cp /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo.service /etc/systemd/system/Primo.AI.Api.MachineInfo.service
   # sudo systemctl daemon-reload
   ```
1. Помещаем службу в автозапуск:
   ```
   # sudo systemctl enable /etc/systemd/system/Primo.AI.Api.MachineInfo.service
   ```
	
## Даем права на запуск

1. Назначаем права:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo
   ```
1. Проверяем выполнение команды:
   ```
   # sudo lsblk --nodeps -no serial /dev/sda
   ```

   Если команда выполнится с ошибкой, находим вместо `/dev/sda` другое блочное устройство (диск) и прописываем его в конфигурационном файле:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-devices.png>)


## Настройка службы
Открываем порт:
```
# sudo ufw allow 5052/tcp
```

## Вспомогательные компоненты
Устанавливаем пакет (команда ОС) cpuid:
```
# cd /srv/samba/shared/install
# sudo dpkg -i cpuid_20201006-1_amd64.deb
```

## Настройка Primo RPA AI Server для работы с MachineInfo

1. Если используется один сервер с MachineInfo, в конфигурационном файле службы Primo.AI.Api прописываем ссылку на него:

   ![](<../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-4.png>)
 
   Параметр **Timeout** – время ответа, после которого сервис считается недоступным. По умолчанию равен 4 сек.

2. Если используется кластер MachineInfo, или MachineInfo используется в геокластере, то в конфигурационном файле службы Primo.AI.Api прописываем ссылки на все узлы кластера:

   ![](<../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-5.png>)

   Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. 

   Узлы нельзя скрывать за балансировщиком нагрузки (load balancer).


## Запускаем службу

1. Запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api.MachineInfo
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.MachineInfo
   ```

## Что дальше

Теперь вы можете перейти к установке UI на машине сервера.
