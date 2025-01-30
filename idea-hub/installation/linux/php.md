# PHP

Проверяем, установлен ли на целевой машине PHP:
```
php --version
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

Если используется ОС Астра Линукс, то требуется произвести обновление репозитория:
```
astra-ce https://dl.astralinux.ru/astra/stable/1.7_x86-64/repository-extended/
```

### Установка пакета и модулей PHP

Выполняем команду:
```
sudo apt install php8.1
```

Устанавливаем необходимые модули:
1. php8.1-imagick
   ```
   sudo apt install php8.1-imagick
   ```
1. php8.1-pgsql
   ```
   sudo# apt install php8.1-pgsql
   ``` 
1. php8.1-fpm
   ```
   sudo apt install php8.1-fpm
   ```
1. php8.1-gd
   ```
   sudo apt install php8.1-gd
   ``` 
1. php8.1-gd
   ```
   sudo apt install php8.1-xml
   ``` 
1. php8.1-curl
   ```
   sudo apt install php8.1-curl
   ``` 
1. php8.1-opcache самой новой версии (8.1.12-1ubuntu4.3).
   ```
   sudo apt install php8.1-opcache
   ``` 
1. php-yaml (2.0.2+1.3.1-4)
   ```
   sudo apt install php-yaml
   ``` 
1. php-pear (1:1.10.13+submodules+notgz+2022032202-2)
   ```
   sudo apt install php-pear
   ```
1. php8.1-apcu
   ```
   sudo apt install php-apcu
   ```
1. php8.1-ldap
   ```
   apt install php8.1-ldap
   ```

## Что дальше

Следует проверить ...
