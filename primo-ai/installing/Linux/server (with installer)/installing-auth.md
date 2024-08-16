# Установка Primo.AI.Api.Auth (с использованием установщика).


1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Запускаем инсталлятор:
   ```
   # /srv/samba/shared/install/Api.Auth-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установим владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api.Auth
   ```

## Опционально - редактируем конфигурационный файл

1. Открываем конфигурационный файл в vim:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```

1. Опционально — настраиваем Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/auth/auth-3.png>)


## Запускаем службу

1. Даем права на запуск службы:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Auth/Primo.AI.Api.Auth
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Auth
   ```
1. При необходимости - запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api.Auth
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Inference.
