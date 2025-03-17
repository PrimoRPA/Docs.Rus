# Установка AutoDoc на OC Linux

## Установка компонентов

С расширенной информацией об установке Linux в Windows с помощью WSL можно ознакомиться [на сайте](https://learn.microsoft.com/ru-ru/windows/wsl/install).

1. Откройте командную строку PowerShell или Windows в режиме администратора  
```
wsl --install
```
затем перезапустите компьютер.

2. Запускаем и определяем пользователя по умолчанию
```
wsl.exe -d Ubuntu
```

3. Установка JAVA
Чтобы автоматически установить самую свежую версию OpenJDK (она уже есть в официальном репозитории Ubuntu):

* Обновите пакеты apt:
```
sudo apt update
```
* Проверяем наличие  java и её инсталляторов
```
$ java -version
Command 'java' not found, but can be installed with:
sudo apt install default-jre              # version 2:1.17-75, or
sudo apt install openjdk-17-jre-headless  # version 17.0.12+7-1ubuntu2~24.04
sudo apt install openjdk-21-jre-headless  # version 21.0.4+7-1ubuntu2~24.04
sudo apt install openjdk-19-jre-headless  # version 19.0.2+7-4
sudo apt install openjdk-20-jre-headless  # version 20.0.2+9-1
sudo apt install openjdk-22-jre-headless  # version 22~22ea-1
sudo apt install openjdk-11-jre-headless  # version 11.0.24+8-1ubuntu3~24.04.1
sudo apt install openjdk-8-jre-headless   # version 8u422-b05-1~24.04
```
* ставим любую из перечисленных версий, например,
```
$ sudo apt install openjdk-8-jre-headless
```
* Проверяем установку версии
```
$ java -version
openjdk version "1.8.0_442"
OpenJDK Runtime Environment (build 1.8.0_442-8u442-b06~us1-0ubuntu1~24.04-b06)
OpenJDK 64-Bit Server VM (build 25.442-b06, mixed mode)
```
* Проверяем переменную среды
```
$ echo $JAVA_HOME
```
* Задаем переменную среды `JAVA_HOME`
  * Открываем проводник
  explorer.exe .
  * Находим папку с java в проводнике
  ```
  \\wsl.localhost\Ubuntu\usr\lib\jvm
  ```
  * Вводим команду для определения переменной среды (вконце пути пишем название папки из 3.6.2)
 ```
 JAVA_HOME="/usr/lib/jvm/jjava-8-openjdk-amd64"
```
* Проверяем переменную среды
```
 $ echo $JAVA_HOME
```

## Обновление до wsl2

4.1 Откройте Командную строку PowerShell или Windows в режиме администратора
wsl --set-default-version 2
4.2 Проверяем 
wsl --status
Распределение по умолчанию: Ubuntu
Версия по умолчанию: 2

или
wsl -l -v
  NAME      STATE           VERSION
\* Ubuntu    Stopped         2

Если версия не 2, то 
wsl --set-version Ubuntu 2(
________________________________________________________________
Запускаем Ubuntu
________________________________________________________________
Открываем explorer.exe .
Также можно использовать команду powershell.exe /c start .. Обязательно добавьте точку в конце команды, чтобы открыть текущий каталог.

создаем каталог для Автодока и копируем туда публикацию для линукс
копируем папку с проектом
Если нужно, копируем пользовательские шаблоны

пробиваем права для текущей директории и -R -рекурсивно по child-ам (.) - текущий директорий
sudo chmod 777 -R .

ls -l - запустить после sudo - покажет всё зеленым - значит сработало - ок

ls -la, чтобы отобразить список файлов прямого доступа и сведения об их создании
ls -l, которая показывает содержимое директории
| - соединяем команды
ls -l | grep Primo - первая, листит каталог. Вторая фильтрует все содержащее "Primo"

-----------------------------------------------------------------------------------------------------------------------
Пример запуска автодока на линукс:
linux-x64/PrimoAutodoc -i Source/ПроектРаспоряжения -o Target -word -local
