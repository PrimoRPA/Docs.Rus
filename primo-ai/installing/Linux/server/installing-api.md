# Установка Primo.AI.Api

1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем папку `/app/Primo.AI/Api`:
   ```
   # sudo mkdir /app/Primo.AI/Api
   ```
1. Разархивируем `Api-linux.zip` в `/app/Primo.AI/Api`:
   ```
   # sudo unzip /srv/samba/shared/install/Api-linux.zip -d /app/Primo.AI/Api
   ```
1. Установим владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api
   ```

## Создаем и настраиваем службу
	
1. Копируем файл службы, который идет с комплектом поставки, в `/etc/systemd/system`:
   ```
   # sudo cp /app/Primo.AI/Api/Primo.AI.Api.service /etc/systemd/system/Primo.AI.Api.service
   ```
1. Перезагружаем systemctl:
   ```
   # sudo systemctl daemon-reload	
   ```
1. Помещаем службу в автозапуск:	
   ```
   # sudo systemctl enable /etc/systemd/system/Primo.AI.Api.service 	
   ```

## Редактируем конфигурационный файл

1. Открываем в vim конфигурационный файл:
   ```
   # sudo nano appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
   ```
   "DBVendor": "Postgres", //Postgres, MSSQL
   ```
1. Редактируем строки подключения к БД:

   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-1.png>)
 
   > *Cм. инструкцию по установке PostgreSQL.*

   В **HOST** указываем адрес сервера, где установлен PostgreSQL.	

   В **USER ID** указываем пользователя БД `primo`, в **PASSWORD** — его пароль.

1. Настраиваем Primo.AI.Api на работу с сервисом получения параметров оборудования для лицензирования — вводим адрес этого сервиса:

   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-2.png>)
 
1. Настраиваем подключение к RabbitMQ:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-3.png>)

1. Опционально — настраиваем MinIO:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-4.png>)

1. Опционально — настраиваем Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-5.png>)

1. Настраиваем параметр `Security > EnabledOrigins` для кроссдоменных запросов:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-6.png>)

   
## Размещаем файлы ИИ-моделей

1. Разархивируем **IDP models.zip** из комплекта поставки в директорию с ИИ-моделями (см. конфигурационный файл: **FileUpload** > **Model** > **Folder**):
   ```
   "FileUpload": {
      ...
      "Model": {
         ...
         "Folder": "/app/Primo.AI/Api_Models" 
      },
      ...
   }
   ```
   
   Для этого выполняем:
   ```
   # sudo unzip '/srv/samba/shared/install/IDP models.zip' -d /app/Primo.AI/Api_Models 	
   ```

## Запускаем службу
1. Даем права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api/Primo.AI.Api
   ```
1. Запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Auth.
