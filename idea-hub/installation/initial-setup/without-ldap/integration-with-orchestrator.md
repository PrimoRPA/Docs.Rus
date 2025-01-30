# Подключение к Оркестратору

Подключение к Оркестратору выполняет системный администратор при наличии соответствующих навыков.

//Для этого у нас есть пакет get-data, распространяется отдельным дистрибутивом и лежит на диске с Идеа хабом. Ссылка есть на диске примо. 

Распаковываем архив, настраиваем синхронизацию с идеа хабом: подключаемся к БД и т.д.

## Настройка прав доступа к каталогам и файлам

### Файлы и каталоги подключения к Оркестратору

1. Добавить пользователя, от имени которого запускается cron в группу **www-data**. Предположим, что это пользователь с именем **ideahub**:
```
sudo usermod -a -G www-data ideahub
```
2. Назначить папке `scripts/orc-data-fetch` и всем файлам внутри владельца ideahub и группу **www-data**. 
Дать право на запись группе.

```
sudo chown ideahub:www-data scripts/orc-data-fetch -R
sudo chgrp ideahub:www-data scripts/orc-data-fetch -R
sudo chmod ug+w scripts/orc-data-fetch -R
```
3. Дать права на запуск файла `scripts/orc-data-fetch/get_data.sh` пользователю и группе **www-data**:
```
sudo chmod ug+x scripts/orc-data-fetch/get_data.sh
```
4. Дать права на запись в каталог, указанный в переменной `OUTPUT_FOLDER` в файле `scripts/orc-data-fetch/.env`:
```
sudo chown www-data OUTPUT_FOLDER
sudo chgrp www-data OUTPUT_FOLDER
sudo chmod ug+w OUTPUT_FOLDER
```
В командах выше, `OUTPUT_FOLDER` нужно заменить на путь, который указан в файле `scripts/orc-data-fetch/.env`.


### Скрипт drupal_fix_permissions.sh

Данный скрипт устанавливает корректные доступы к файлам и каталогам IdeaHub. Для использования скрипта необходим `sudo` доступ. 

Стоит принять во внимание, что если какая-либо папка (private, files или другие) отсутствует, то скрипт не покажет ошибки.

1. Скачать [здесь](https://github.com/Metadrop/drupal-fix-permissions-script/blob/main/drupal_fix_permissions.sh) скрипт.

2. Ознакомиться с документацией встроенной в этот скрипт. Можно посмотреть, если запустить скрипт с параметром `--help`.
   ```
   sudo bash drupal_fix_permissions.sh --help
   ```
3. Определить группу от которой работает ваш сервер, зачастую это `www-data` (найти универсальный способ определения).

4. Желательно чтобы пользователь, который владеет папкой с проектом и пользователь, который запускает `cron` совпадали (нужно обозначить, что должен быть специальный пользователь, например **ideahub**, от имени которого и установка и обновления и пр.).

5. Основные опции команды это:
   - ```-u``` пользователь.
   - ```-g``` группа.
   - ```-f``` путь до папки private из папки `web`.
   - ```-p``` полный путь до папки `web` проекта.

В итоге команда будет иметь вид:
```
sudo bash ./scripts/drupal_fix_permissions.sh -p=/var/www/ideahub/web -u=ideahub -g=www-data -f="../config -f="../private" -sp="../scripts"
```

