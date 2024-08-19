# Установка Primo.AI.Api.Inference  (с использованием установщика).


1. Подключаемся к серверу по SSH с пользователем с правами root. 
1. Запускаем инсталлятор:
   ```
   # /srv/samba/shared/install/Api.Inference-X.X.X.X.run
   ```
1. По завершению работы инсталлятора установим владельца папки с инсталляцией:
   ```
   # sudo chown -R primo:primo-ai /app/Primo.AI/Api.Inference
   ```

## Опционально - редактируем конфигурационный файл
1. Открываем для редактирования конфигурационный файл:
   ```
   # sudo vim appsettings.ProdLinux.json
   ```   
1. Опционально – настраиваем Redis:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/inference/inference-3.png>)


## Запускаем службу

1. Даем права на запуск:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.Inference/Primo.AI.Api.Inference
   ```
1. Проверяем состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.Inference
   ```
1. При необходимости - запускаем службу:
   ```
   # sudo systemctl start Primo.AI.Api.Inference
   ```

## Что дальше

Теперь вы можете перейти к установке компонента Api.Logs.
