# Мультитенантность
Оркестратор может функционировать в мультитенантном варианте - под тенантом подразумевается относительно независимый экземпляр Оркестратора. Например, если организация состоит из обособленных подразделений/филиалов, то этому подразделению/филиалу можно назначить тенант.

Мультитенантность настраивается в конфигурационном файле WebApi в секции **Tenants**:

![](<../../.gitbook/assets/tenants-config.png>) 

#### Таблица 1 – Описание параметров для настройки мультитенантности.

| Параметр | Назначение | Примечание |
| -------- | ---------- | ---------- |
| FromAppsettings | Всегда должно быть true | Зарезервировано для новых версий Оркестратора |
| TimeOffset | Смещение времени в часах от стандартного времени для отображения в журнале Робота и Оркестратора для дефолтного тенанта |   |
| IncomingEmail | Параметры ящика для получения почты для дефолтного тенанта  | Пароль шифруется при помощи программы LTools.Orchestrator.PasswordEncriptor.exe  |
| Items      | Массив тенантов |   |
| Items[].Id | Идентификатор тенанта  | Также используется при конфигурировании агента на машине Робота  |
| Items[].Name | Наименование тенанта |   |
| Items[].TimeOffset | То же что и № п/п 2, только для не дефолного тенанта |   |
| Items[].IncomingEmail | То же что и № п/п 3, только для не дефолного тенанта |   |

Если используется SSO, то привязка тенантов к AD также настраивается в секции **ActiveDirectory**:

```json
"ActiveDirectory": {
    "KerberosKeytabPath": "C:\\Primo\\krb5.keytab",
    "Type": 5,
    "MultyForest": {
      "primo1.orch": {
        "ConnectionTimeout": 2000,
        "Host": "185.247.193.52",
        "UseSsl": false,
        "AcceptUntrustedCertificate": false,
        "AdminUserName": "Administrator@primo1.orch",
        "AdminPassword": "JLWIyl1xZNDVVx8tcVllOg==",
        "StartPoint": "CN=Users,DC=primo1,DC=orch",
        "UserFilterTemplate": "(&(objectCategory=user)(objectClass=user)(userPrincipalName={0}))",
        "GroupsFilter": "(&(ObjectClass=group))",
        //"GroupsFilter": "(&(ObjectClass=group)(|(cn=primo)(cn=another)))",
        "Tenants": [ "", "BUCH" ],
      },
```

В массиве Tenants перечисляются ID тенантов, которые привязаны к AD. Пустая строка – это ID дефолтного тенанта.


		
	
		
	
	
	

