# Настройка прав доступа к каталогам и файлам

В этом разделе описывается, как настроить права доступа к файлам и каталогам подключения к Оркестратору.

1. В группу **www-data** добавьте пользователя, от имени которого запускается cron. Предположим, что это пользователь с именем **ideahub**.

   Сналача войдите в систему под пользователем **ideahub**, иначе команда добавления не сработает. Можно использовать sudo доступ:
   ```
   sudo su ideahub
   ```

   После чего добавьте пользователя командой:
   ```
   sudo usermod -a -G www-data ideahub
   ```

2. Назначьте папке `scripts/orc-data-fetch` и всем её файлам владельца **ideahub** и группу **www-data**. Дайте право на запись группе.
   ```
   sudo chown ideahub:www-data scripts/orc-data-fetch -R
   sudo chgrp ideahub:www-data scripts/orc-data-fetch -R
   sudo chmod ug+w scripts/orc-data-fetch -R
   ```
3. Дайте права на запуск файла `scripts/orc-data-fetch/get_data.sh` пользователю и группе **www-data**:
   ```
   sudo chmod ug+x scripts/orc-data-fetch/get_data.sh
   ```
4. Дайте права на запись в каталог, указанный в переменной `OUTPUT_FOLDER` в файле `scripts/orc-data-fetch/.env`:
   ```
   sudo chown www-data OUTPUT_FOLDER
   sudo chgrp www-data OUTPUT_FOLDER
   sudo chmod ug+w OUTPUT_FOLDER
   ```

   В командах выше нужно заменить `OUTPUT_FOLDER` на путь, который указан в файле `scripts/orc-data-fetch/.env`.
