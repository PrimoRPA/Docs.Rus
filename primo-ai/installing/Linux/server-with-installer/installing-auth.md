# Установка Primo.AI.Api.Auth 

В этом разделе вы узнаете, как с помощью инсталлятора установить на машину сервера компонент Primo.AI.Api.Auth.

1. Подключитесь к серверу по SSH с пользователем с правами root. 
1. Запустите инсталлятор:
   ```
   # /srv/samba/shared/install/Api.Auth-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установите владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api.Auth
   ```

## Опционально — отредактируйте конфигурационный файл

1. Откройте конфигурационный файл в vim:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```

1. Опционально — настройте Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/auth/auth-3.png>)


## Запускаем службу

1. Назначьте права на запуск службы:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Auth/Primo.AI.Api.Auth
   ```
1. Проверьте состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Auth
   ```
1. При необходимости — запустите службу:
   ```
   # sudo systemctl start Primo.AI.Api.Auth
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Inference.
