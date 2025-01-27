# Установка на ОС Linux

Установка и настройка окружения выполняется на машине с операционной системой Linux (Ubuntu, Debian).
		
## PHP

Проверяем, установлен ли на целевой машине PHP:
```
$ php --version
```

Пример результата выполнения команды:
```
PHP 8.2.5 (cli) (built: May 3 2023 05:10:17) (NTS)  
Copyright (c) The PHP Group  
Zend Engine v4.2.5, Copyright (c) Zend Technologies    
with Zend OPcache v8.2.5, Copyright (c), by Zend Technologies    
with Xdebug v3.2.1, Copyright (c) 2002-2023, by Derick Rethans
```
Если результат аналогичен примеру, а также демонстрирует, что на компьютере установлен PHP версии 8.1 или выше, можно переходить к следующему этапу установки. 

Если версия PHP ниже 8.1 или пакет не установлен, необходимо обновить или установить его. 

В случае ОС Астра Линукс требуется произвести обновление репозитория:
```
astra-ce https://dl.astralinux.ru/astra/stable/1.7_x86-64/repository-extended/
```

### Установка пакета и модулей PHP

Выполните команду:
```
$ sudo apt install php8.1
```
Установите необходимые модули:
1. php8.1-imagick
   ```
   $ sudo apt install php8.1-imagick
   ```
1. php8.1-pgsql
   ```
   $ sudo# apt install php8.1-pgsql
   ``` 
1. php8.1-fpm
   ```
   $ sudo apt install php8.1-fpm
   ```
1. php8.1-gd
   ```
   $ sudo apt install php8.1-gd
   ``` 
1. php8.1-gd
   ```
   $ sudo apt install php8.1-xml
   ``` 
1. php8.1-curl
   ```
   $ sudo apt install php8.1-curl
   ``` 
1. php8.1-opcache самой новой версии (8.1.12-1ubuntu4.3).
   ```
   $ sudo apt install php8.1-opcache
   ``` 
1. php-yaml (2.0.2+1.3.1-4)
   ```
   $ sudo apt install php-yaml
   ``` 
1. php-pear (1:1.10.13+submodules+notgz+2022032202-2)
   ```
   $ sudo apt install php-pear
   ```
1. php8.1-apcu
   ```
   $ sudo apt install php-apcu
   ```
1. php8.1-ldap
   ```
   apt install php8.1-ldap
   ```


## PostgreSQL

Проверяем, установлен ли на целевой машине PostgreSQL:

```
$ psql –version
```

Если версия PostgreSQL >= 13, то переходим к пункту **Настройка базы данных**.

В противном случае производим установку PostgreSQL:
```
$ sudo apt install postgresql postgresql-contrib
```

После установки postgresql необходимо откорректировать конфигурационные файлы:

1. `/etc/postgresql/14/main/postgresql.conf` — в этом файле изменения производятся только в том случае, если рассматривается возможность подключения к БД Idea Hub по сети.

   Находим строку:
   ```
   listen_addresses = 'localhost'
   ```
   И меняем значение, чтобы сервер БД слушал подключения на всех локальных интерфейсах:
   ```
   listen_addresses = '*'
   ``` 
   Или чтобы сервер БД слушал подключения на конкретном интерфейсе:
   ```
   listen_addresses = 'IP-address'
   ```

1. `/etc/postgresql/14/main/pg_hba.conf`

   Вносим следующие изменения в соответствии с политиками безопасности предприятия:

   ```local   all             all				md5``` 

   Позволяет любому пользователю локальной системы подключаться к базе данных "postgres", если он передает правильный пароль.

   ```host    all             all             192.168.12.10/24	md5```

   Позволяет любому пользователю компьютера 192.168.12.10 подключаться к базе данных "postgres", если он передаёт правильный пароль.

Перезапускаем PostgreSQL:

 ```
 $ sudo systemctl reastart postgresql
```
 ```
 $ sudo systemctl status postgresql
```

## Настройка базы данных

Войдем в **psql** под пользователем **postgres**:

```
$ sudo -i -u postgres
```
```
$ psql
```

Создаем нового пользователя PostgreSQL (вместо password указываем свой пароль):

```
CREATE USER primo_ideahub WITH PASSWORD 'password';
```

Создаем базу данных и добавляем нужные привилегии:
```
CREATE DATABASE ideahub OWNER primo_ideahub;
GRANT ALL PRIVILEGES ON DATABASE ideahub TO primo_ideahub;
CREATE EXTENSION pg_trgm;
```

Выход из psql:
```
postgres=# \q
```

Рестарт сервера:
```
$ sudo service postgresql restart
```

## Установка и настройка Drush (CLI административный модуль)

Создаем пользователя, который будет запускать скрипты:
```
$ sudo adduser ideahub
```

Добавляем пользователя в группу **www-data**:
```
$sudo usermod -a -G www-data ideahub
```

////Настройка заработает только после того, как мы впервые зайдём за данного пользователя.

Создаем каталог для установки Idea Hub с определенными правами (группе и владельцу разрешено читать и писать) и устанавливаем владельцами этого каталога пользователя **ideahub** и группу **www-data**:

```
$ sudo mkdir -m gu+rw -p  /var/www/ideahub
```
* **-m** – устанавливает права доступа к создаваемым каталогам
* **-p** – создает родительские каталоги с заданными правами

```
$ sudo chown ideahub:www-data /var/www/ideahub
```

Установочный архив Idea Hub должен быть предварительно загружен в каталог `/home/ideahub`.

Распаковываем архив в каталог `/var/www/ideahub/:`
```
$ tar -xzf idea-hub.install.24.6.6.linux.tar.gz -C /var/www/ideahub/
```

Меняем владельца и группу для всех вложенных папок и файлов рабочего каталога:
```
$sudo chown -R ideahub:www-data /var/www/ideahub
```

## Установка Idea Hub

В каталоге `/var/www/ideahub/db` находится дамп базы данных `/var/www/ideahub/db/ideahub_demo.sql.gz`. Название файла может отличаться. 

1. Восстанавливаем базу данных PostgreSQL из этого файла командой:
   ```
   gunzip -c /var/www/ideahub/db/ideahub_demo.sql.gz | psql -U primo_ideahub -d ideahub
   ```
   Будет предложено ввести пароль для пользователя **primo_ideahub**. Вводим пароль, установленный для этого пользователя в разделе **Настройка базы данных**.

   После восстановления базы данных каталог `/var/www/ideahub/db` можно удалить.

1. Далее настроиваем папки и права. Можно вводить команды вручную, как это описано ниже, либо использовать скрипт `drupal_fix_permissions` — [инструкция](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/installation-linux#skript-drupal_fix_permissions.sh) по использованию скрипта приведена внизу страницы. 

   В каталоге `web/sites/default/` создаем папку `files` и настраиваем для нее права:
   ```
   $ mkdir /var/www/ideahub/web/sites/default/files
   $ cd /var/www/ideahub
   $ chgrp -Rv www-data web/sites/default/files
   $ chmod 2775 web/sites/default/files
   $ chmod g+w -R web/sites/default/files
   $ chmod 444 web/sites/default/settings.php
   ```
1. В `/var/www/ideahub/` создаем каталог `private` и настроиваем для него права:
   ```
   $ cd /var/www/ideahub
   $ mkdir private
   $ chgrp -Rv www-data private
   $ chmod 2775 private
   $ chmod g+w -R private
   ```
1. Входим в систему под служебным пользователем пользователем **ideahub**.

1. Копируем файл `/var/www/ideahub/config/settings.EXAMPLE.php` в `/var/www/ideahub/config/settings.local.php`.

   После чего меняем в новом файле строки: ```HOST, DATABASE_NAME, USER_NAME, PASSWORD``` на установленные во время создания базы данных.

   Пример:
   ```
   $databases['default']['default'] = [
   'driver' => 'pgsql',
   'autoload' => 'core/modules/pgsql/src/Driver/Database/pgsql/',
   'namespace' => 'Drupal\\pgsql\\Driver\\Database\\pgsql',
   'prefix' => '',
   'port' => '5432',
   'host' => 'localhost',
   'database' => 'ideahub',
   'username' => 'primo_ideahub',
   'password' => 'password',
   ];
   ```
   где 'password' — пароль пользователя primo_ideahub, установленный в секции **Настройка базы данных**.

1. Переходим в папку проекта:
   ```
   $ cd /var/www/ideahub
   ```

1. Добавляем ссылку на `drush` глобально — для этого надо добавить данную строку в конец файла ```~/.bashrc``` в домашнем каталоге пользователя, из под которого будут запускаться скрипты (в нашем случае /home/ideahub):
   ```
   $ export PATH="/var/www/ideahub/vendor/bin:$PATH"
   ```
   Обновление данных вашего терминала:
   ```
   $ source ~/.bashrc
   ```
1. Проверяем подключение к базе данных командой:
   ```
   $ drush status
   ```

Результат должен быть следующего вида:
```shell
Drupal version   : 9.5.10-dev
Site URI         : https://ideahub-v2.lndo.site/
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
```
Если это так, то ваш сайт успешно установлен.

После этого очистите кеш командой:
```
$ drush cr
```

## Настройка окружения

Как установить максимальный размер загружаемого файла:
1. Заранее обговорите с компетентными лицами максимальный размер файлов, которые можно будет загружать.
2. Настройте конфиг Nginx. У **nginx.conf** (`/etc/nginx/nginx.conf`) надо поправить значение _**client_max_body_size**_. Для 100 мегабайт значением будет 100M.
3. Настройте конфигурацию PHP. В **php.ini** (`/etc/php/8.1/fpm/php.ini`) надо поправить значения: **_upload_max_filesize_** и _**post_max_size**_. Для 100 мегабайт значением будет 100M.
4. Далее следует настроить поля друпала. К примеру для поля "Документы", контент типа процесс, надо перейти по адресу `/admin/structure/types/manage/process/fields/node.process.field_docs` и редактировать значение в поле "Максимальный размер закачки". Для 100 мегабайт значением будет 100MB.


## Установка и настройка web-сервера Nginx

1. Установка NGINX:
   ```
   $ sudo apt install nginx
   ```
1. Копируем файл `./config/ideahub-nginx.conf` в каталог `/etc/nginx/sites-available`.

1. Редактируем файл `/etc/nginx/sites-available/ideahub-nginx.conf`, заменив в нём значение DOMAIN_NAME на имя домена, который вы будете использовать при подключении к серверу через браузер (в нашем примере ideahub.local): 

   ```
   server_name ideahub.local;
   ```

   Cтроку `root /var/www/DOMAIN_NAME/web;` замените на:
   ```
   root /var/www/ideahub/web;
   ```

1. Найдите строки типа `fastcgi_pass unix:/run/php/php8.2-fpm.sock` и раскомментируйте ту, в которой указана ваша версия PHP.

1. Добавьте сайт в список включенных командой:
   ```
   $ sudo ln -s /etc/nginx/sites-available/ideahub-nginx.conf /etc/nginx/sites-enabled/ideahub-nginx.conf
   ```
1. Перезапустите Nginx:
   ```
   $ sudo systemctl restart nginx
   ```

## Настройка доступа через браузер

Теперь вашей локальной машине нужно дать доступ к сайту.

1. Найдите файл `hosts`.
   - В Windows он находится по адресу **c:\windows\system32\drivers\etc\hosts**; потребуется админский доступ.
   - В Linux он находится по адресу **/etc/hosts**, потребуется административный доступ.
1. Добавьте в конец файла строку типа:
   ```
   192.168.1.121 ideahub.local
   ```

   Где `192.168.1.121` - это IP-адрес тестового стенда с Idea Hub, а `ideahub.local` - это домен, который вы указали ранее в секции "Установка и настройка web-сервера Nginx".


### Установка обновлений для релиза 24.12
1. ```drush migrate:import params_ru --update```
2. ```drush migrate:import library_items --execute-dependencies --update```
3. ```drush ev "require_once (\Drupal::root() . '/../scripts/RandomContent.php');(new RandomContent())->createDashboards();"```

## Проверка установки
1) Войдите в систему как admin.
2) Перейдите на страницу статуса проекта - /admin/reports/status
3) При наличии "Ошибок" или "Предупреждений" об этом **НЕОБХОДИМО** сообщить разработчикам.
4) Разработчики сообщат о том какие вещи необходимо исправить и скорее всего подключатся для помощи.

## Настройка прав доступа к каталогам и файлам

### Файлы и каталоги подключения к Оркестратору

1. В группу **www-data** добавляем пользователя, от имени которого запускается cron. Предположим, что это пользователь с именем **ideahub**.

   Сналача войдем в систему под пользователем **ideahub**, иначе команда добавления не сработает. Можно использовать sudo доступ:
   ```
   sudo su ideahub
   ```

   После чего добавляем пользователя командой:
   ```
   sudo usermod -a -G www-data ideahub
   ```

2. Назначаем папке `scripts/orc-data-fetch` и всем её файлам владельца **ideahub** и группу **www-data**. Даем право на запись группе.
   ```
   sudo chown ideahub:www-data scripts/orc-data-fetch -R
   sudo chgrp ideahub:www-data scripts/orc-data-fetch -R
   sudo chmod ug+w scripts/orc-data-fetch -R
   ```
3. Даем права на запуск файла `scripts/orc-data-fetch/get_data.sh` пользователю и группе **www-data**:
   ```
   sudo chmod ug+x scripts/orc-data-fetch/get_data.sh
   ```
4. Даем права на запись в каталог, указанный в переменной `OUTPUT_FOLDER` в файле `scripts/orc-data-fetch/.env`:
   ```
   sudo chown www-data OUTPUT_FOLDER
   sudo chgrp www-data OUTPUT_FOLDER
   sudo chmod ug+w OUTPUT_FOLDER
   ```

   В командах выше нужно заменить `OUTPUT_FOLDER` на путь, который указан в файле `scripts/orc-data-fetch/.env`.


### Скрипт drupal_fix_permissions.sh

Скрипт устанавливает корректные доступы к файлам и каталогам Idea Hub. Для использования скрипта необходим `sudo` доступ. 

Стоит принять во внимание, что если какая-либо папка (private, files или другие) отсутствует, то скрипт не покажет ошибки.

Чтобы воспользоваться скриптом:

1. [Скачайте](https://github.com/Metadrop/drupal-fix-permissions-script/blob/main/drupal_fix_permissions.sh) скрипт.
2. Ознакомьтесь с документацией, встроенной в этот скрипт. Документацию можно посмотреть, если запустить скрипт с параметром `--help`.
   ```
   sudo bash drupal_fix_permissions.sh --help
   ```
3. Определите группу, от которой работает ваш сервер. Зачастую это **www-data** (найдите универсальный способ определения).
4. Желательно, чтобы пользователь, который владеет папкой с проектом, и пользователь, который запускает `cron`, совпадали. Нужно обозначить, что должен быть специальный пользователь, например **ideahub**, от имени которого выполняется и установка, и обновления, и т.п.
5. Основные опции команды:
   - ```-u``` пользователь.
   - ```-g``` группа.
   - ```-f``` путь до папки private из папки `web`.
   - ```-p``` полный путь до папки `web` проекта.

В итоге команда будет иметь вид:
```
sudo bash ./scripts/drupal_fix_permissions.sh -p=/var/www/ideahub/web -u=ideahub -g=www-data -f="../config -f="../private" -sp="../scripts"
```


