# Установка и настройка веб-сервера Nginx

1. Установите Nginx:
   ```
   sudo apt install nginx
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
   sudo ln -s /etc/nginx/sites-available/ideahub-nginx.conf /etc/nginx/sites-enabled/ideahub-nginx.conf
   ```
1. Перезапустите Nginx:
   ```
   sudo systemctl restart nginx
   ```

## Настройка доступа через браузер

Теперь вашей локальной машине нужно дать доступ к сайту.

1. Найдите файл `hosts`. В Linux он находится по адресу **/etc/hosts**, потребуется административный доступ.
1. Добавьте в конец файла строку типа:
   ```
   192.168.1.121 ideahub.local
   ```

   Где `192.168.1.121` — это IP-адрес тестового стенда с Idea Hub, а `ideahub.local` — это домен, который вы указали ранее при установке и настройке веб-сервера Nginx.


## Что дальше

Следующий шаг:
* Опционально — [проверка установки](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/installation/linux/shecking-installation).
