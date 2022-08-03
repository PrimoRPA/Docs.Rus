# Ручная установка и запуск робота Core

Робот Core представляет собой кроссплатформенную версию робота Primo

**Установка в Ubuntu**

1. Перейдите в магазин приложений Ubuntu (Ubuntu Store)

![](<../../.gitbook/assets/image (930).png>)

&#x20; 2\. Установите пакет .NET Runtime 5.0

![](<../../.gitbook/assets/image (973).png>)

3\. Выполнить

```
sudo apt install -y libgdiplus libc6 libc6-dev
sudo apt install -y fontconfig libharfbuzz0b libfreetype6
```

4\. Перейдите в папку робота и предоставьте файлу Primo.Robot права на запуск

![](<../../.gitbook/assets/image (853).png>)

&#x20; 5\. Перейдите в папку WebDriver и предоставьте всем файлам права на запуск

![](<../../.gitbook/assets/image (755).png>)

&#x20; 6\.  Можете запускать робота из терминала, например:

```
./Primo.Robot instantStart noOrchestrator "projPath=/home/primo/Downloads/Core" "seqPath=/home/primo/Downloads/Core/Main.ltw"

```
