# Установка Primo.AI.Api.Auth


## Размещаем файлы компонента

1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.Auth`:
   ```
   sudo mkdir -p /app/Primo.AI/Api.Auth
   ```
1. Разархивируем `Api.Auth-linux.zip` в `/app/Primo.AI/Api.Auth`:	
   ```
   sudo unzip /srv/samba/shared/install/distr/Api.Auth-linux.zip -d /app/Primo.AI/Api.Auth
   ```
1. Установите владельца папки с инсталляцией:
   ```
   sudo chown -R primo:primo-ai /app/Primo.AI/Api.Auth
   ```

## Создаем и настраиваем службу
	 
1. Копируем файл службы из комплекта поставки в `/etc/systemd/system`:
   ```
   sudo cp /app/Primo.AI/Api.Auth/Primo.AI.Api.Auth.service /etc/systemd/system/Primo.AI.Api.Auth.service
   ```
1. Перезагружаем systemctl:
   ```
   sudo systemctl daemon-reload	
   ```
1. Помещаем службу в автозапуск:	
   ```
   sudo systemctl enable /etc/systemd/system/Primo.AI.Api.Auth.service
   ```
	

## Редактируем конфигурационный файл

1. Открываем конфигурационный файл в vim:
   ```
   sudo nano appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
    ```
    "DBVendor": "Postgres", //Postgres, MSSQL
    ```
 1. Редактируем строки подключения к БД:

    ![](<../../../../.gitbook/assets1/primo-ai/install/auth/auth-1.png>)
   
    > *Cм. инструкцию по установке PostgreSQL.*

    В `HOST` указываем адрес сервера, где установлен PostgreSQL.	

    В `USER ID` указываем пользователя БД `primo`, а в `PASSWORD` — его пароль.

1. Настраиваем подключение к RabbitMQ:

   ![](<../../../../.gitbook/assets1/primo-ai/install/auth/auth-2.png>)

1. Опционально — настраиваем Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/auth/auth-3.png>)


## Запускаем службу

1. Даем права на запуск:

   ```
   sudo chmod -R 770 /app/Primo.AI/Api.Auth/Primo.AI.Api.Auth
   ```
1. Запускаем службу:
   ```
   sudo systemctl start Primo.AI.Api.Auth
   ```
1. Проверяем состояние службы:
   ```
   sudo systemctl status Primo.AI.Api.Auth
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Inference.
