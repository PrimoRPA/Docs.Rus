# Установка на машине с операционной системой Windows
		
  ### PHP
1. Распакуйте файлы PHP8.2.zip в папку C:\PHP
2. Добавьте путь C:\PHP в переменные окружения PATH в Windows
3. Дайте права пользователям на «Изменение» (создание и удаление) в данном каталоге C:\PHP
	
 ### PostgreSQL
1. Установите PostgreSQL
   ***postgresql-13.11-2-windows-x64.exe***
2. Создайте базу данных и пользователя в интерфейсе PgAdmin через Query Tools:  
***CREATE USER primo_ideahub WITH PASSWORD 'password';***  
***CREATE DATABASE ideahub OWNER primo_ideahub;***  
***GRANT ALL PRIVILEGES ON DATABASE ideahub TO primo_ideahub;***  
***ALTER USER 'primo_ideahub' SUPERUSER;***  
***CREATE EXTENSION pg_trgm;***
3. Добавьте C:\Program Files\PostgreSQL\13\bin в переменные окружения PATH в Windows
4. Распакуйте архив с дампом БД в каталоге C:\nginx\html\IdeaHub\db
5. Восстановите БД из дампа   
***C:\nginx\html\IdeaHub\db***  
***.\psql -h localhost -p 5432 -d ideahub -U postgres -f ideahub_demo.sql***
   
### Nginx
1. Распакуйте файлы nginx.zip в папку C:\nginx
2. Добавьте путь C:\nginx\html\IdeaHub\vendor\drush\drush в переменные окружения PATH в Windows 
3. Добавьте путь C:\nginx в переменные окружения PATH в Windows
4. Распакуйте IdeaHub.zip в каталог C:\nginx\html\IdeaHub 
5. Дайте права пользователям на «Изменение» (создание и удаление) в каталоге C:\nginx\html\IdeaHub
   
### Конфигурирование
Скопируйте с названием settings.local.php и заполните конфигурационный файл \config\settings.EXAMPLE.php

1. Данные соединения БД:
'port' => '5432',
'host' => 'HOST',
'database' => 'DATABASE_NAME',
'username' => 'USER_NAME',
'password' => 'PASSWORD',

2. Директории для хранения файлов
   
-$settings['file_temp_path'] = 'C:\nginx\html\IdeaHub\private';  
-$settings['file_private_path'] = ' C:\nginx\html\IdeaHub\private';

3. Доменные имена сайта:
-$settings['trusted_host_patterns'] = [
  '^ideahub-v2\.lndo\.site',

Пример заполнения (сайт доступен по адресу ideahub.local, localhost, по имени машины):
$settings['trusted_host_patterns'] = [
  '^ideahub\.local',
  '^localhost',
  '^MACHINE_NAME',

### Запуск
1. Запустите C:\nginx\start-php-fcgi.bat
2. Запустите C:\nginx\nginx.exe
3. Проверьте подключение к базе данных в cmd  
***cd C:\nginx\html\IdeaHub***  
***drush status***  

Результат должен быть примерно таким:

![](<../../.gitbook/assets/IdeaHub_Installation_1.png>)


