# Установка Api.Logs 

В этом разделе вы узнаете, как с помощью инсталлятора установить на машину сервера компонент Api.Logs.

1. Подключитесь к серверу по SSH с пользователем с правами root. 
1. Запустите инсталлятор:
   ```
   /srv/samba/shared/install/Api.Logs-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установите владельца папки с инсталляцией:
   ```
   sudo chown -R primo:primo-ai /app/Primo.AI/Api.Logs
   ```

## Запустите службу

1. Назначьте права на запуск:
   ```
   sudo chmod -R 770 /app/Primo.AI/Api.Logs/Primo.AI.Api.Logs
   ```
1. Проверьте состояние службы:
   ```
   sudo systemctl status Primo.AI.Api.Logs
   ```
1. При необходимости — запустите службу:
   ```
   sudo systemctl start Primo.AI.Api.Logs
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.MachineInfo.
