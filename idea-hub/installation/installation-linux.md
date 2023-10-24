# Установка на машине с операционной системой Linux (Ubuntu, Debian)
		
## PHP

На данном этапе проверьте, установлен ли на целевой машине PHP, и его версию. Это можно сделать, введя следующую команду из командной строки:

```
# php --version
```

Пример результата выполнения команды:
```  
PHP 8.2.5 (cli) (built: May 3 2023 05:10:17) (NTS)  
Copyright (c) The PHP Group  
Zend Engine v4.2.5, Copyright (c) Zend Technologies    
with Zend OPcache v8.2.5, Copyright (c), by Zend Technologies    
with Xdebug v3.2.1, Copyright (c) 2002-2023, by Derick Rethans
```

Если результат выполнения команды выглядит аналогично примеру, приведенному выше, и демонстрирует, что на компьютере установлен PHP версии 8.1 или выше, переходите к  следующему этапу установки. 
Если версия PHP ниже 8.1 или отсутствует, установите или обновите ее, обновив репозитории:

```
# apt-get install php php-imagick php-pgsql php-fpm php-gd php-xml php-curl php-opcache php-yaml php-devel php-pear php-apcu
```

## PostgreSQL

Проверьте, установлен ли на целевой машине PostgreSQL:

```
# postgres --version
```
 
Пример вывода команды:
```
postgres (PostgreSQL) 14.3*
```
Если вывод команды выглядит похожим образом и версия PostgreSQL >= 13, то переходите к следующему этапу установки.
При отсутствии на машине PostgreSQL установите его, используя команду

 ```
 # apt-get install postgresql postgresql-contrib
```


## Настройка базы данных:

1. В файле `/etc/postgresql/14/main/pg_hba.conf` (номер версии укажите тот, который установлен на машине) поменяйте строку  
```
editorconfig  
local all all peer  
```  
на  
```
editorconfig  
local all all md5
``` 
 
2. Запустите сервер с помощью команды  
```
 # service postgresql start
 ```
3. Войдите в административный интерфейс, используя пользователя `postgres`:
```
# sudo -i -u postgres  
# psql
```
4. Создайте нового пользователя PostgreSQL (вместо "password" укажите свой пароль):  
```
# postgresql    
# CREATE USER primo_ideahub WITH PASSWORD 'password';
```  
5. Создайте базу данных и добавьте нужные привилегии:  
```
# postgresql    
# CREATE DATABASE ideahub OWNER primo_ideahub;
# GRANT ALL PRIVILEGES ON DATABASE ideahub TO primo_ideahub;    
# CREATE EXTENSION pg_trgm;
```

## Установка Drush (CLI административный модуль) 

Drush уже установлен в каталоге проекта. Требуется добавить возможность запускать его командой `drush`, для этого выполните
```
# ln -s PROJECT_PATH/vendor/drush/drush/drush /usr/bin/drush
```

## Конфигурирование

1. Распакуйте полученный архив с файлами IdeaHub в каталог `/var/www/DOMAIN_NAME/`
2. В каталоге `/var/www/DOMAIN_NAME/db` находится дамп базы данных `/var/www/DOMAIN_NAME/db/idea-hub.29062023-16-12-30.sql.gz` (название файла может отличаться).
Восстановите базу данных PostgreSQL из этого файла командой   
```
# gunzip -c /var/www/DOMAIN_NAME/db/idea-hub.29062023-16-12-30.sql.gz | psql -U
# primo_ideahub DATABASE_NAME
```
3. После восстановления базы данных каталог `/var/www/DOMAIN_NAME/db` можно удалить.
4. Настройте права для каталога `web/sites/default/files`, который находится в `/var/www/DOMAIN_NAME/`  
```
# cd /var/www/DOMAIN_NAME    
# chgrp -Rv www-data web/sites/default/files  
# chmod 2775 web/sites/default/files  
# chmod g+w -R web/sites/default/files  
# chmod 444 web/sites/default/settings.php
```
5. Настройте права для каталога `private`, который находится в `/var/www/DOMAIN_NAME/`
```
# cd /var/www/DOMAIN_NAME  
# chgrp -Rv www-data private  
# chmod 2775 private  
# chmod g+w -R private
```
6. Скопируйте файл  `/var/www/DOMAIN_NAME/config/settings.EXAMPLE.php` в `/var/www/DOMAIN_NAME/config/settings.local.php` 
и замените в новом файле строки: `HOST`, `DATABASE_NAME`, `USER_NAME`, `PASSWORD` на установленные во время создания базы данных на шаге 2.   
В этом же файле найдите настройку `$settings['trusted_host_patterns']` и укажите в ней значение в соответствие с описанием. Остальные настройки в этом файле можно оставить по умолчанию.
7. Проверьте подключение к базе данных командой  
```
# cd /var/www/DOMAIN_NAME    
# drush status
```

Результат должен быть примерно таким:  

	Drupal version   : 9.5.10-dev  
	Site URL         : https://ideahub-v2.lndo.site/  
	DB driver        : pgsql  
	DB hostname      : database  
	DB port          : 5432  
	DB username      : postgres  
	DB name          : drupal9  
	Database         : Connected  
	Drupal bootstrap : Successful  
	Default theme    : orcx2  
	Admin theme      : gin  
	PHP binary       : /usr/local/bin/php  
	PHP OS           : Linux  
	PHP version      : 8.2.5  
	Drush script     : /app/vendor/bin/drush  
	Drush version    : 11.7.0-dev  
	Drush temp       : /tmp  
	Drush configs    : /app/vendor/drush/drush/drush.yml  
	Install profile  : standard  
	Drupal root      : /app/web  
	Site path        : sites/default  
	Files, Public    : sites/default/files  
	Files, Private   : ../private  
	Files, Temp      : /tmp  


Если это так, то ваш сайт успешно установлен.
