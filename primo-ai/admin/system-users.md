# Встроенные роли и пользователи

Ниже приводятся учетные записи и роли, которые встроены в систему для упрощения ее настройки и администрирования. 


## Встроенные роли

Встроенные роли предназначены для решения административных задач и предоставляют пользователю расширенные права доступа. Невозможно создать вручную роли, аналогичные встроенным, поэтому для пользователей-администраторов должны использоваться только встроенные роли. 

| Встроенная роль       | Описание                                         |  Примечание |
| --------------------- | ------------------------------------------------ | ------------ | 
| Administrator         | Кросстенантная административная роль\*. Предоставляет пользователю полные полномочия как в рамках тенанта по умолчанию, так и в любом другом тенанте. <br> Пользователь с данной ролью имеет право управлять лицензиями и пользователями всех тенантов, в том числе создавать пользователей с административными правами </br> | По умолчанию роль Administrator уже имеют пользователи **superadmin** и **admin**.  Это встроенные пользователи, которые настраивают систему для использования рядовыми пользователями |
| TenantAdministrator   | Аналогично роли Administrator, но только в рамках своего тенанта | По умолчанию никто из пользователей не имеет этой роли |


## Встроенные пользователи

Встроенные пользователи создаются при первом запуске приложения. По своему назначению эти учетные записи можно разделить на административные и служебные.

### Администраторы

:bangbang: *После первого входа в систему обязательно смените пароль.*

| Логин     | Пароль            | Роль               | Описание                                         |  
| ----------------------- | ----------------- | ------------------ | ----------------------------- |
| superadmin              | Qwe123!@#         | Administrator      | Предоставляет полный набор прав для управления и настройки системы. Кросстенантный пользователь  |
| admin                   | Qwe123!@#         | Administrator      | Аналогично полномочиям superadmin, но действует в рамках тенанта по умолчанию. Не имеет прав в других тенантах |


### Службы

Служебные учетные записи обеспечивают взаимодействие между компонентами системы и не подразумевают участие человека. Данные пользователи кросстенантны.


| Логин      | Пароль            | Роль               | Описание                                                           |  
| ----------------------- | ----------------- | ------------------ | ------------------------------------------------------------------ |
| agent                   | Qwe123!@#         | Agent              | Для взаимодействия Primo.AI.Api.Agent с другими сервисами Primo.AI |
| api                     | Qwe123!@#         | Api                | Для взаимодействия Primo.AI.Api с другими сервисами Primo.AI       |
| auth                    | Qwe123!@#         | Auth               | Для взаимодействия Primo.AI.Api.Auth с другими сервисами Primo.AI  |
| inference               | Qwe123!@#         | Inference          | Для взаимодействия Primo.AI.Api.Inference с другими сервисами Primo.AI |
| logs                    | Qwe123!@#         | Logs               | Для взаимодействия Primo.AI.Api.Logs с другими сервисами Primo.AI |



