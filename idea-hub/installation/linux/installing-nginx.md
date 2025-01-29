# Установка и настройка веб-сервера Nginx

1. Установите Nginx:
   ```
   $ sudo apt install nginx
   ```
1. Скопируйте файл `./config/ideahub-nginx.conf` в каталог `/etc/nginx/sites-available`.

1. Отредактируйте файл `/etc/nginx/sites-available/ideahub-nginx.conf`, заменив в нём значение DOMAIN_NAME на имя домена, который вы будете использовать при подключении к серверу через браузер (в нашем примере ideahub.local): 

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
