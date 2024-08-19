# Установка Primo.AI.Api.Inference 

В этом разделе вы узнаете, как с помощью инсталлятора установить на машину сервера компонент Primo.AI.Api.Inference.

1. Подключитесь к серверу по SSH с пользователем с правами root. 
1. Запустите инсталлятор:
   ```
   # /srv/samba/shared/install/Api.Inference-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установите владельца папки с инсталляцией:
   ```
   # sudo chown -R primo:primo-ai /app/Primo.AI/Api.Inference
   ```

## Опционально — отредактируйте конфигурационный файл

1. Откройте для редактирования конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```   
1. Опционально — настройте Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/inference/inference-3.png>)


## Запускаем службу

1. Назначьте права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Inference/Primo.AI.Api.Inference
   ```
1. Проверьте состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Inference
   ```
1. При необходимости — запустите службу:
   ```
   # sudo systemctl start Primo.AI.Api.Inference
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Logs.
