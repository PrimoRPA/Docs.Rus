# Установка Primo.AI.Api.Logs 

## Размещаем файлы компонента
1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI`. 
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.Logs`:
   ```
   # sudo mkdir /app/Primo.AI/Api.Logs
   ```
1. Разархивируем `Api.Logs-linux.zip` в `/app/Primo.AI/Api.Logs`:
   ```
   # sudo unzip /srv/samba/shared/install/Api.Logs-linux.zip -d /app/Primo.AI/Api.Logs
   ```
1. Установите владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api.Logs
   ```

## Создаем и настраиваем службу
	
1. Копируем файл службы из комплекта поставки в `/etc/systemd/system`:
   ```
   # sudo cp /app/Primo.AI/Api.Logs/Primo.AI.Api.Logs.service /etc/systemd/system/Primo.AI.Api.Logs.service
   # sudo systemctl daemon-reload
   ```
1. Помещаем службу в автозапуск:
   ```
   # sudo systemctl enable /etc/systemd/system/Primo.AI.Api.Logs.service 	
   ```

## Редактируем конфигурационный файл

1. Открываем конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
   ```
   "DBVendor": "Postgres", //Postgres, MSSQL
   ```
 
1. Редактируем строки подключения к БД:

 
   > *Cм. инструкцию по установке PostgreSQL.*

   В `HOST` указываем адрес сервера, где установлен PostgreSQL.	

   В `USER ID` указываем пользователя БД `primo`, а в `PASSWORD` – его пароль.


1. Настраиваем подключение к RabbitMQ:
 


## Запускаем службу

1. Даем права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Logs/Primo.AI.Api.Logs
   ```
1. Стартуем службу:
   ```
   # sudo systemctl start Primo.AI.Api.Logs
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Logs
   ```
