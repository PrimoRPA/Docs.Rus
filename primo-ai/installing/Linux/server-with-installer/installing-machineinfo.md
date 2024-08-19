# Установка Primo.AI.Api.MachineInfo

В этом разделе вы узнаете, как с помощью инсталлятора установить на машину сервера компонент Primo.AI.Api.MachineInfo.

1. Подключитесь к серверу по SSH с пользователем с правами root. 
1. Запустите инсталлятор:
   ```
   # /srv/samba/shared/install/Api.MachineInfo-X.X.X.X.run
   ```
1. По завершению работы инсталлятора назначьте владельца папки с инсталляцией:
   ```
   #  sudo chown -R primo:primo-ai /app/Primo.AI/Api.MachineInfo
   ```

## Назначение прав на запуск

1. Назначьте права:
   ```
   # sudo chmod -R 770 /app/Primo.AI/Api.MachineInfo/Primo.AI.Api.MachineInfo
   ```
1. Проверьте выполнение команды:
   ```
   # sudo lsblk --nodeps -no serial /dev/sda
   ```

   Если команда выполнится с ошибкой, найдите вместо `/dev/sda` другое блочное устройство (диск) и пропишите его в конфигурационном файле:
 
   ![](<../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-devices.png>)


## Настройка службы
Откройте порт:
```
# sudo ufw allow 5052/tcp
```

## Вспомогательные компоненты
Установите пакет (команда ОС) cpuid:
```
# cd /srv/samba/shared/install
# sudo dpkg -i cpuid_20201006-1_amd64.deb
```

## Настройка Primo RPA AI Server для работы с MachineInfo

1. Если используется один сервер с MachineInfo, в конфигурационном файле службы Primo.AI.Api пропишите ссылку на него:

   ![](<../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-4.png>)
 
   Параметр **Timeout** – время ответа, после которого сервис считается недоступным. По умолчанию равен 4 сек.

2. Если используется кластер MachineInfo, или MachineInfo используется в геокластере, то в конфигурационном файле службы Primo.AI.Api пропишите ссылки на все узлы кластера:

   ![](<../../../../.gitbook/assets1/primo-ai/install/MachineInfo/MachineInfo-5.png>)

   Порядок узлов имеет значение. В момент генерации запроса на лицензию должны быть доступны все узлы. 

   Узлы нельзя скрывать за балансировщиком нагрузки (load balancer).


## Запуск службы

1. Проверьте состояние службы:
   ```
   # sudo systemctl status Primo.AI.Api.MachineInfo
   ```

1. При необходимости — запустите службу:
   ```
   # sudo systemctl start Primo.AI.Api.MachineInfo
   ```

## Что дальше

Теперь вы можете перейти к установке UI на машине сервера.
