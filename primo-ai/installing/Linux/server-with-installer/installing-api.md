# Установка Primo.AI.Api (с использованием установщика).

1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Запускаем инсталлятор:
   ```
   # /srv/samba/shared/install/Api-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установим владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api
   ```


## Опционально — редактируем конфигурационный файл

1. Открываем в vim конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```

1. Настраиваем Primo.AI.Api на работу с сервисом получения параметров оборудования для лицензирования — вводим адрес этого сервиса:

   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-2.png>)

1. Опционально — настраиваем MinIO:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-4.png>)

1. Опционально — настраиваем Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-5.png>)


## Запускаем службу
1. Даем права на запуск службы:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api/Primo.AI.Api
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api
   ```
1. При необходимости - запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api
   ```


## Что дальше

Теперь вы можете перейти к установке компонента Api.Auth.
