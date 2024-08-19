# Обновление ПО

## Обновление агента
Остановите службу:
```
# sudo systemctl stop Primo.AI.Agent
```

Обновите файлы агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
# sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /app/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json

# sudo chown -R agent:primo-ai /app/Primo.AI/Agent

# sudo chmod -R 771 /app/Primo.AI/Agent /app/Primo.AI/AgentData

# sudo chown -R  agent:primo-ai /app/Primo.AI/Agent
```

Запустите службу:
```
# sudo systemctl start Primo.AI.Agent
```
Просмотр статуса службы:
```
# sudo systemctl status Primo.AI.Agent
```

## Обновление IDP

Создайте резервную копию текущей установки. 

Удалите текущую установку – папку `src`:
```
# sudo rm -r /app/Primo.AI/IDP/src
```

Обновите файлы IDP на целевой машине (файл `A-IDP.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
# sudo unzip -o -u /srv/samba/shared/install/A-IDP.zip -d /app/Primo.AI/IDP -x start_inference.sh start_training.sh  start_evaluation.sh venv.zip

# sudo chown -R  idp:primo-ai /app/Primo.AI/IDP

# sudo chmod -R 771 /app/Primo.AI/IDP
```