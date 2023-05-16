# Мультитенантность
Оркестратор может функционировать в мультитенантном варианте - под тенантом подразумевается относительно независимый экземпляр Оркестратора. Например, если организация состоит из обособленных подразделений/филиалов, то этому подразделению/филиалу можно назначить тенант.

Мультитенантность настраивается в конфигурационном файле WebApi в секции **Tenants**:

![](<../../.gitbook/assets/tenants-config.png>) 

#### Таблица 1 – Описание параметров для настройки мультитенантности.

| Параметр | Назначение | Примечание |
| -------- | ---------- | ---------- |
| FromAppsettings | Всегда должно быть `true` | Зарезервировано для новых версий Оркестратора |
| TimeOffset | Смещение времени в часах от стандартного времени для отображения в журнале Робота и Оркестратора для дефолтного тенанта |   |
| IncomingEmail | Параметры ящика для получения почты для дефолтного тенанта  |  |
| Agent  | Параметры обращения к агенту   |   |
| Items      | Массив тенантов |   |
| Items[].Id | Идентификатор тенанта  | Также используется при конфигурировании агента на машине Робота  |
| Items[].Name | Наименование тенанта |   |
| Items[].TimeOffset | То же что и параметр `TimeOffset`, только для недефолного тенанта |   |
| Items[].IncomingEmail | То же что и параметр `IncomingEmail`, только для недефолного тенанта |   |
| Items[].Agent  | То же что и параметр `Agent`, только для недефолного тенанта    | За счет этой настройки можно на одной машине робота развернуть несколько агентов для разных тенантов. Каждый агент будет слушать входящие запросы на своем порту  |
| IncomingEmail.UserName  | Пользователь – полное имя почтового ящика. Например, primo.rpa@mail.ru   |   |
| IncomingEmail.Password  | Пароль к почтовому ящику   | Пароль шифруется при помощи программы LTools.Orchestrator.PasswordEncriptor.exe (входит в поставку)  |
| IncomingEmail.Pop3  | Адрес Pop3-сервера. Например, pop.mail.ru   | Если используется Imap, то не заполняется  |
| IncomingEmail.Pop3Port  | Порт Pop3-сервера. Например, 995   | Если используется Imap, то не заполняется  |
| IncomingEmail.RequireAuthenticate  | Определяет, требуется ли аутентификация |   |
| IncomingEmail.UseSsl  | Используется ли SSL/TLS/STARTTLS   |   |
| IncomingEmail. UseStandartNotSSLPort  | Используется [стандартный порт](https://github.com/jstedfast/MailKit/blob/master/FAQ.md#SslHandshakeException ). В этом случае игнорируется флаг UseSsl   |   |
| IncomingEmail.Imap  | Адрес Imap-сервера. Например, imap.mail.ru   | Если используется Pop3, то не заполняется  |
| IncomingEmail.ImapPort  | Порт Imap-сервера. Например, 993   |  Если используется Pop3, то не заполняется  |
| IncomingEmail.ImapFolder  | Папка с письмами. Например, INBOX   |  Если используется Pop3, то не заполняется  |

Если используется SSO, то привязка тенантов к AD также настраивается в секции **ActiveDirectory** в параметре **Tenants**:

```json
"ActiveDirectory": {
    "KerberosKeytabPath": "C:\\Primo\\krb5.keytab",
    "Type": 5,
    "MultyForest": {
      "primo1.orch": {
        "Host": "185.247.193.52",
        "AdminUserName": "Administrator@primo1.orch",
        "AdminPassword": "JLWIyl1xZNDVVx8tcVllOg==",
        "StartPoint": "CN=Users,DC=primo1,DC=orch",
        "UserFilterTemplate": "(&(objectCategory=user)(objectClass=user)(userPrincipalName={0}))",
        "GroupsFilter": "(&(ObjectClass=group))",
        "Tenants": [ "", "BUCH" ],
      },
```

В массиве Tenants перечисляются ID тенантов, которые привязаны к AD. Пустая строка – это ID дефолтного тенанта.


		
	
		
	
	
	

