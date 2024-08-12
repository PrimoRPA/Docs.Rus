# Установка Primo.AI.Api.Inference 

## Размещаем файлы компонента

1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Создаем, если отсутствует, папку `/app/Primo.AI`.
1. Создаем, если отсутствует, папку `/app/Primo.AI/Api.Inference`:
   ```
   # sudo mkdir /app/Primo.AI/Api.Inference
   ```
1. Разархивируем `Api.Inference-linux.zip` в `/app/Primo.AI/Api.Inference`:
   ```
   # sudo unzip /srv/samba/shared/install/Api.Inference-linux.zip -d /app/Primo.AI/Api.Inference
   ```
1. Установите владельца папки с инсталляцией:
   ```
   # sudo chown -R primo:primo-ai /app/Primo.AI/Api.Inference
   ```

## Создаем и настраиваем службу
	 
1. Копируем файл службы из комплекта поставки в `/etc/systemd/system`:
   ```
   # sudo cp /app/Primo.AI/Api.Inference/Primo.AI.Api.Inference.service /etc/systemd/system/Primo.AI.Api.Inference.service
   # sudo systemctl daemon-reload	
1. Помещаем службу в автозапуск:
   ```
   # sudo systemctl enable /etc/systemd/system/Primo.AI.Api.Inference.service
   ```

## Редактируем конфигурационный файл
1. Открываем для редактирования конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```
1. Задаем тип используемой СУБД:
 
1. Редактируем строки подключения к БД:

 
   > *Cм. инструкцию по установке PostgreSQL.*
   
   В `HOST` указываем адрес сервера, где установлен PostgreSQL.	
   
   В `USER ID` указываем пользователя БД primo, а в `PASSWORD` – его пароль.


1. Настраиваем подключение к RabbitMQ:
 

1. Опционально - настраиваем Redis:
 

## Запускаем службу

1. Даем права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Inference/Primo.AI.Api.Inference
   ```
1. Стартуем службу:
   ```
   # sudo systemctl start Primo.AI.Api.Inference
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Inference
   ```

