# Настройка базы и доступов к файлам

1. Восстановите базу данных PostgreSQL из этого файла командой:
   ```
   gunzip -c /var/www/ideahub/db/ideahub_demo.sql.gz | psql -U primo_ideahub -d ideahub
   ```
   Система предложит ввести пароль для пользователя **primo_ideahub**. Введите пароль, который был установлен для этого пользователя в разделе **Настройка базы данных**.

   После восстановления базы данных каталог `/var/www/ideahub/db` можно удалить.

1. Далее настраиваем папки и права. Можно вводить команды вручную, как это описано ниже, либо использовать скрипт `drupal_fix_permissions` — см. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/linux/drupalfixpermissions).

   В каталоге `web/sites/default/` создайте папку `files` и настройте для нее права:
   ```
   mkdir /var/www/ideahub/web/sites/default/files
   cd /var/www/ideahub
   chgrp -Rv www-data web/sites/default/files
   chmod 2775 web/sites/default/files
   chmod g+w -R web/sites/default/files
   chmod 444 web/sites/default/settings.php
   ```
1. В `/var/www/ideahub/` создайте каталог `private` и настройте для него права:
   ```
   cd /var/www/ideahub
   mkdir private
   chgrp -Rv www-data private
   chmod 2775 private
   chmod g+w -R private
   ```
1. Войдите в систему под служебным пользователем **ideahub**.

1. Скопируйте файл `/var/www/ideahub/config/settings.EXAMPLE.php` в `/var/www/ideahub/config/settings.local.php`.

1. Измените в новом файле строки: ```HOST, DATABASE_NAME, USER_NAME, PASSWORD``` на установленные во время создания базы данных.

   Пример:
   ```
   databases['default']['default'] = [
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
   где 'password' — пароль пользователя **primo_ideahub**, который вы установили при **Настройке базы данных**.

1. Перейдите в папку проекта:
   ```
   cd /var/www/ideahub
   ```
1. Проверьте подключение к базе данных командой:
   ```
   drush status
   ```

Результат должен иметь вид:
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
drush cr
```

## Обновление базы данных

Релизы Idea Hub могут поставляться без последних обновлений базы данных. Например, минорные релизы, в которых происходят незначительные исправления.

Поэтому при установке Idea Hub дополнительно запустите команды:
 ```
 drush updb -y
```
```
drush locale:import ru /полный/путь/до/web/translations/custom.ru.po --override=all
```
```
drush pcta ru
```
```
drush cr
```

Также для корректной работы с дашбордами в Idea Hub требуется выполнить следующие действия с библиотекой панелей:

1. [Скачайте](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FIdeaHub) архив **libraries-items-20241203-1048.tgz** и разархивируйте его по адресу `/path/to/project/web/sites/default/files`.
2. Установите владельца и группу для этой папки:
   ```
   chown -R ideahub:www-data ./web/sites/default/files/libraries_items
   ```
3. Выполните команду:
   ```
   drush migrate:rollback covers
   ```
5. Выполните команду импорта:
   ```
   drush migrate:import library_items --execute-dependencies --update
   ```



## Что дальше

Следующий шаг — [настройка окружения](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/linux/setting-up-environment).

