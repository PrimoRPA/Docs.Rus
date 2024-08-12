# Установка Primo.AI.Api.MachineInfo 

## Размещаем файлы компонента
1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI`.
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.MachineInfo`:
   ```
   # sudo mkdir /app/Primo.AI/Api.MachineInfo
   ```
1. Разархивируем `Api.MachineInfo-linux.zip` в `/app/Primo.AI/Api.MachineInfo`:
   ``` 
   # sudo unzip /srv/samba/shared/install/Api.MachineInfo-linux.zip -d /app/Primo.AI/Api.MachineInfo
   ```
1. Установите владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api
   ```

## Создаем и настраиваем службу
	 
1. Копируем файл службы (идет с комплектом поставки) в /etc/systemd/system:
   ```
   # sudo cp /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo.service /etc/systemd/system/Primo.AI.Api.MachineInfo.service
   # sudo systemctl daemon-reload
   ```
1. Помещаем службу в автозапуск:
   ```
   # sudo systemctl enable /etc/systemd/system/Primo.AI.Api.MachineInfo.service
   ```
	
## Редактируем конфигурационный файл
1. Открываем конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
 
1. Редактируем строки подключения к БД:

 
   > *Cм. инструкцию по установке PostgreSQL.*

   В HOST указываем адрес сервера, где установлен PostgreSQL.	
   
   В USER ID указываем пользователя БД primo. В PASSWORD – его пароль.


1. Настраиваем подключение к RabbitMQ:
 


1. Опционально - настраиваем Redis:
 

## Даем права на запуск
1. Даем права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo
   ```
1. Проверяем выполнение команды:
   ```
   # sudo lsblk --nodeps -no serial /dev/sda
   ```

   Если она выполнится с ошибкой, находим вместо `/dev/sda` какое-то другое блочное устройство (диск) и прописываем его в конфигурационном файле:
 


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
Если используется один сервер с MachineInfo, в конфигурационном файле службы Primo.AI.Api прописывается ссылка на него:
 
Параметр `Timeout` (по умолчанию 4 сек) – время ответа, после которого сервис считается не доступным.
Если используется кластер MachineInfo, или MachineInfo используется в геокластере, в конфигурационном файле службы Primo.AI.Api прописываются ссылки на все узлы кластера:
 
Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. 

Узлы нельзя скрывать за лоадбалансером.


## Запускаем службу

1. Запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api.MachineInfo
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.MachineInfo
   ```
