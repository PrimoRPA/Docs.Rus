# Установка Primo.AI.Api

В этом разделе вы узнаете, как с использованием установщика установить на машину сервера компонент Primo.AI.Api.


1. Подключитесь к серверу по SSH с пользователем с правами root. 
1. Запустите инсталлятор:
   ```
   # /srv/samba/shared/install/Api-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установите владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api
   ```


## Опционально — отредактируйте конфигурационный файл

1. Откройте в vim конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```

1. Настройте Primo.AI.Api на работу с сервисом получения параметров оборудования для лицензирования — введите адрес этого сервиса:

   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-2.png>)

1. Опционально — настройте MinIO:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-4.png>)

1. Опционально — настройте Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/api/API-5.png>)


## Запустите службу
1. Назначьте права на запуск службы:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api/Primo.AI.Api
   ```
1. Проверьте состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api
   ```
1. При необходимости - запустите службу:
   ```
   # sudo systemctl start Primo.AI.Api
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Auth.
