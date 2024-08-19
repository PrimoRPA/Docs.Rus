# Установка Primo.AI.Api.Logs (с использованием установщика).

1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Запускаем инсталлятор:
   ```
   # /srv/samba/shared/install/Api.Logs-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установим владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api.Logs
   ```


## Запускаем службу

1. Даем права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Logs/Primo.AI.Api.Logs
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Logs
   ```
1. При необходимости - запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api.Logs
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.MachineInfo.
