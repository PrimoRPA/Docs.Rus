# Интеграция с Active Directory

Интеграция со службо1 Active Directory (далее - AD) осуществляется следующим образом:

1. Front Сервис Оркестратора регистрируется в AD и DNS (см. таблица 2, № п/п 27 **ВСТАВИТЬ ССЫЛКУ ИЛИ НАЗВАНИЕ ДОКИ**). 
2. В зависимости от ОС и варианта развертывания (см. раздел [Развертывание сервера приложений Оркестратора](**CCЫЛКА**)):
   * Для Windows 2016 Server и варианта развертывания **WebApi и Front работают под IIS** сервер с IIS может быть включен в AD. Тогда в IIS для узла Primo.WebApi должна быть разрешена аутентификация Windows, а пул приложений этого узла должен работать под доменной SPN учетной записью, полученной при регистрации сервиса в AD:

   ![](<../../.gitbook/assets/6. Разрешение аутентификация Windows для узлов в IIS.png>)

   ![](<../../.gitbook/assets/7. Пользователь, под которым работает пул приложений Primo.WebApi.png>)

   * Для ОС Linux, или варианта развертывания для Windows 2016 Server **WebApi – служба Windows, Front – nginx**, или если сервер с IIS не включен в AD – только на основе keytab-файла. 

3. В конфигурационном файле WebApi в секции **ActiveDirectory** нужно прописать настройки для каждого AD, чтобы в UI Оркестратора роль Оркестратора могла быть ассоциирована с группой AD:

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
        "TrustedDomains": []
      },
      "primo2.orch": {
        "ConnectionTimeout": 2000,
        "Host": "185.247.193.88",
        "AdminUserName": "Administrator@primo2.orch",
        "AdminPassword": "JLWIyl1xZNDVVx8tcVllOg==",
        "StartPoint": "CN=Users,DC=primo2,DC=orch",
        "UserFilterTemplate": "(&(objectCategory=user)(objectClass=user)(userPrincipalName={0}))",
        "GroupsFilter": "(&(ObjectClass=group))",
        //"GroupsFilter": "(&(ObjectClass=group)(|(cn=primo)(cn=another)))",
        "Tenants": [ "" ],
        "TrustedDomains": []
      }
    }
  },
```
Для AD-групп в параметре **GroupsFilter** может быть произведена более точная фильтрация, например, по названиям групп:

* Путем явного перечисления через ИЛИ:

`(&(ObjectClass=group)(|(cn=primo)(cn=another)))`

* С использованием регулярного выражения:

`(&(ObjectClass=group)(cn=prim*))`

Если фильтрация не используется, может возникнуть ошибка при запросе сильно большого количества групп.

Если не используется одновременно несколько AD, лишний AD должен быть удален.

Наименование AD в конфигурационном файле WebApi рекомендуется выбирать в соответствии со значениями DC в StartPoint, например, для primo1.orch DC=primo1, DC=orch.

В таблице 9 приведено описание параметров для настройки AD, которые администратор может менять:

