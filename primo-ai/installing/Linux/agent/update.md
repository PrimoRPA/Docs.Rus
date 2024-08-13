# Обновление

## Обновление агента
Остановка службы:
```
# sudo systemctl stop Primo.AI.Agent
```

Обновление файлов агента на целевой машине (файл `Agent-linux.zip` должен находиться в каталоге `/srv/samba/shared/install`):
```
# sudo unzip -o -u /srv/samba/shared/install/Agent-linux.zip -d /app/Primo.AI/Agent -x appsettings.ProdLinux.json appsettings.json

# sudo chown -R agent:primo-ai /app/Primo.AI/Agent

# sudo chmod -R 771 /app/Primo.AI/Agent /app/Primo.AI/AgentData

# sudo chown -R  agent:primo-ai /app/Primo.AI/Agent
```

Запуск службы:
```
# sudo systemctl start Primo.AI.Agent
```
Просмотр статуса службы:
```
# sudo systemctl status Primo.AI.Agent
```
