# Установка Primo.AI.Api.Logs 

## Размещаем файлы компонента
1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.Logs`:
   ```
   sudo mkdir /app/Primo.AI/Api.Logs
   ```
1. Разархивируем `Api.Logs-linux.zip` в `/app/Primo.AI/Api.Logs`:
   ```
   sudo unzip /srv/samba/shared/install/Api.Logs-linux.zip -d /app/Primo.AI/Api.Logs
   ```
1. Установите владельца папки с инсталляцией:
   ```
   sudo chown -R primo:primo-ai /app/Primo.AI/Api.Logs
   ```

## Создаем и настраиваем службу
	
1. Копируем файл службы из комплекта поставки в `/etc/systemd/system`:
   ```
   sudo cp /app/Primo.AI/Api.Logs/Primo.AI.Api.Logs.service /etc/systemd/system/Primo.AI.Api.Logs.service
   ```
1. Перезагружаем systemctl:
   ```
   sudo systemctl daemon-reload	
   ```
1. Помещаем службу в автозапуск:
   ```
   sudo systemctl enable /etc/systemd/system/Primo.AI.Api.Logs.service 	
   ```

## Редактируем конфигурационный файл

1. Открываем конфигурационный файл:
   ```
   sudo nano appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
   ```
   "DBVendor": "Postgres", //Postgres, MSSQL
   ```
 1. Редактируем строки подключения к БД:

    ![](<../../../../.gitbook/assets1/primo-ai/install/logs/logs-1.png>)

    > *Cм. инструкцию по установке PostgreSQL.*

    В **HOST** указываем адрес сервера, где установлен PostgreSQL.	

    В **USER ID** указываем пользователя БД `primo`, а в **PASSWORD** – его пароль.


1. Настраиваем подключение к RabbitMQ:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/logs/logs-2.png>)

1. Настраиваем периодичность автоматической очистки БД:
   ```
   "AutoClearService": {
     "PeriodSeconds": 3600, // периодичность запуска сервиса очистки
     "AgentLoadsObsoleteSeconds": 2592000, // через какой период устаревают записи о нагрузке на целевые машины - 30 дней
     "TrainMetricsObsoleteSeconds": null, // через какой период устаревают метрики обучения
     "ApiObsoleteSeconds": null // через какой период устаревает журнал
   }
   ```
При этом очистка заключается в удалении соотв. записей - операцию VACUUM сервис самостоятельно не выполняет.


## Запускаем службу

1. Даем права на запуск:
   ```
   sudo chmod -R 770 /app/Primo.AI/Api.Logs/Primo.AI.Api.Logs
   ```
1. Запускаем службу:
   ```
   sudo systemctl start Primo.AI.Api.Logs
   ```
1. Проверяем состояние службы:
   ```
   sudo systemctl status Primo.AI.Api.Logs
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.MachineInfo.
