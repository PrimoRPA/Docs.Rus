# Настройка хранения секретов служб в отдельной БД

Службы Оркестратора:
1.	WebApi
2.	RobotLogs
3.	States
4.	Notifications
5.	Analytic
могут хранить свои секреты в отдельной БД ltoolssecrets. 

Для этого требуется:
1. В конфигурационный файл служб (appsettings.ProdWin.json или appsettings.ProdLinux.json) добавить (если отсутствует) секцию Secrets с параметром External = true:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/secrets.PNG)

2. Установить переменную окружения\* SecretsConnection со строкой подключения к БД с секретами ltoolssecrets (пароль в строке подключения должен быть зашифрован\*\*, если параметр `Secrets:ConnectionPasswordEncripted` имеет значение `true` – по умолчанию):
`PORT=5432;TIMEOUT=15;POOLING=True;MINPOOLSIZE=1;MAXPOOLSIZE=20;COMMANDTIMEOUT=20;DATABASE=ltoolssecrets;HOST=192.168.1.172;USER ID=postgres;PASSWORD= 49EqQ30zfcQTWxEGYE/mSw==`

>\* - *Может использоваться параметр `Secrets:ConnectionString`. Если он не задан, используется переменная окружения*  
>\*\* - *Здесь и далее пароли шифруются при помощи LTools.Orchestrator.PasswordEncriptor*

3. При запуске служб Оркестратора БД с секретами создастся автоматически, все пароли будут иметь стандартные значения в незашифрованном виде. 
Эти пароли нужно будет заменить своими и зашифровать, параметр `Secrets:PasswordEncripted` установить в `true` – по умолчанию). Секреты хранятся в таблицах:

| №п/п | Служба | Таблица | Примечание |
| --- | --- | --- | --- |
| 1. | WebApi | WebApi | В виде пар ключ-значение\* |
| 2. | WebApiAD | Секреты из секции ActiveDirectory: MultyForest для каждого AD |
| 3. | WebApiTenantIncomingEmail | Секреты из секции Tenants:Items для IncomingEmail каждого недефолтного тенанта |
| 4. | RobotLogs | RobotLogs | В виде пар ключ-значение |
| 5. | States | States | В виде пар ключ-значение |
| 6. | Notifications | Notifications | В виде пар ключ-значение |
| 7. | Analytic | Analytic | В виде пар ключ-значение |

>\* - *На основе одноименной иерархии в конфигурационном файле. Например, RabbitMQ:UserName*

4. В конфигурационном файле заменить секреты на заглушки. Например:

![](../../../orchestrator-new/resources/orchestrator-sys-admin/secrets2.PNG)
