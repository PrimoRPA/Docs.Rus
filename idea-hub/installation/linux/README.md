# Установка на ОС Linux

Установка Idea Hub и настройка окружения выполняется на машине с операционной системой Linux: Ubuntu, Debian, Astra Linux. Пошаговый порядок установки приведен ниже.

## Установка и настройка окружения

{% stepper %}
{% step %}
### Установка PHP 
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/php).
{% endstep %}
{% step %}
### Установка PostgreSQL
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/postgresql).
{% endstep %}
{% step %}
### Настройка базы данных
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/setting-up-database).
{% endstep %}
{% endstepper %}

## Установка Idea Hub

{% stepper %}
{% step %}
### Подготовка к установке
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/drush).
{% endstep %}
{% step %}
### Настройка базы и доступов к файлам
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/setting-up-access).
{% endstep %}
{% step %}
### Настройка окружения
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/setting-up-environment).
{% endstep %}
{% step %}
### Установка и настройка веб-сервера Nginx
А также настройка доступа через браузер. Инструкцию см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/installing-nginx).
{% endstep %}
{% step %}
### Опционально — установка обновлений для релиза 24.12
Если вы устанавливаете другую версию Idea Hub, то пропустите этот шаг.
Инструкцию по установке обновления 24.12 см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/installing-updates-for-24.12). 
{% endstep %}
{% step %}
### Проверка установки
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/shecking-installation).
{% endstep %}
{% step %}
### Настройка прав доступа к каталогам и файлам подключения к Оркестратору
См. [инструкцию](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/setting-access-to-orchfiles).
{% endstep %}
{% endstepper %}

Дополнительно:
* Скрипт [drupal_fix_permissions.sh](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-idea-hub/readme-installation/linux/drupalfixpermissions).
* Утилита pass — консольный менеджер паролей.
