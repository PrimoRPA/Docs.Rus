# Установка Primo.AI.Api для Linux

***Это шаг после предв. настр. маш. с Primo RPA AI Server под Astra Linux.

1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI`*.
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
   # sudo systemctl daemon-reload	
   ```
1. Помещаем службу в автозапуск:	
   ```
   # sudo systemctl enable /etc/systemd/system/Primo.AI.Api.service 	
   ```

## Редактируем конфигурационный файл
1. Редактируем конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
1. Редактируем строки подключения к БД:

 
Cм. Рук-во по уст. PostgreSQL.docx.
В HOST указываем адрес сервера, где установлен PostgreSQL.	
В USER ID указываем пользователя БД primo. В PASSWORD – его пароль.
3. Настраиваем Primo.AI.Api на работу с сервисом получения параметров оборудования для лицензирования – вводим адрес этого сервиса:
 
4. Настраиваем подключение к RabbitMQ:
 

5. Опционально - настраиваем MinIO:
 

6. Опционально - настраиваем Redis:
 

7. Настраиваем параметр Security > EnabledOrigins для кроссдоменных запросов:
 

## Даем права на запуск
```
# sudo chmod -R 770 /app/Primo.AI/Api/Primo.AI.Api
```

## Запускаем службу
```
# sudo systemctl start Primo.AI.Api
```

## Проверяем состояние службы
```
# sudo systemctl status Primo.AI.Api
```
>*\*Согласно инструкции по предварительной настройке машины для Primo RPA AI Server под Astra Linux.*
