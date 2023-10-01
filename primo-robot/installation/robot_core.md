# Ручная установка и запуск робота Core

Робот Core представляет собой кроссплатформенную версию робота Primo и поддерживает установку на Linux. 

:bangbang: ***Дистрибутив предоставляется вендором по запросу и имеет ограниченные возможности для работы с UI.***

Ниже приведен пример установки Primo Robot на OC Ubuntu.

### Установка в Ubuntu

Перейдите в магазин приложений Ubuntu (Ubuntu Store):

![](<../../.gitbook/assets/image (176).png>)

Установите пакет .NET Runtime 5.0:

![](<../../.gitbook/assets/image (159).png>)

Выполните команды:

```
sudo apt install -y libgdiplus libc6 libc6-dev
sudo apt install -y fontconfig libharfbuzz0b libfreetype6
```

Перейдите в папку Робота и предоставьте файлу Primo.Robot права на запуск:

![](<../../.gitbook/assets/image (154).png>)

Перейдите в папку WebDriver и предоставьте всем файлам права на запуск:

![](<../../.gitbook/assets/image (92).png>)

### Запуск 

Пример запуска Робота из терминала:

```
./Primo.Robot instantStart noOrchestrator "projPath=/home/primo/Downloads/Core" "seqPath=/home/primo/Downloads/Core/Main.ltw"

```
