# Спецификация WebApi на прием событий Оркестратора

Требуется реализовать WebApi с двумя end-point – для авторизации и для приема событий.\
Все данные в формате JSON (заголовок Content-Type = application/json).

## End-point авторизации
Авторизация по токену (JWT token). Адрес этого end-point задается в настройках сервиса LogEventsWebhook как `HttpEndPoint:LoginUrl`.

POST: LoginUrl 

Данные передаются в теле запроса как объект:
```json
{
     "UserName": "userName",
     "Password": "password"
}
```
Логин и пароль также задаются в настройках сервиса LogEventsWebhook в секции `HttpEndPoint`.\
Возвращается токен в теле ответа в виде объекта:
```json
{
     "Token": "eyJhbGciOiJI…"
}
```

## End-point приема событий
Адрес этого end-point задается в настройках сервиса LogEventsWebhook как `HttpEndPoint:Url`

POST: Url

Данные передаются в теле запроса как объект события (см. таблицу 1):
```
{
     "Id": "955f8b51-00a4-4807-b723-a3e5c547da01",
     "Event": 101,
     ...
}
```
Токен передается в заголовке `Authorization = Bearer \<token\>`

Если end-point приема событий **не допускает** неавторизованный запрос, должен возвращаться http-статус **401 Unauthorized**.\
Если end-point приема событий **допускает** неавторизованный запрос, HttpEndPoint:LoginUrl можно оставить пустым или null.
 
Таблица 1 – Описание свойств объекта события
> *Знак «?» в столбце **Тип** означает, что значение этого типа может быть null.*

| Свойство  | Тип  | Описание  |  
| --------- | ---- | --------- |   
| Id        | Guid | Идентификатор события |   
| Event     | Enum? | Событие. См. поле **Код** в [Приложении 3 - События Оркестратора](https://docs.primo-rpa.ru/primo-rpa/orchestrator/appendix/appendix3) |
| EntityId  | string | Идентификатор сущности, связанной с событием | 
| UserId    | string | Идентификатор пользователя, связанного с событием  | 
| OrchTimestampUtc | DateTime | Время события по времени оркестратора в UTC | 
| OperationKey | Guid? | Идентификатор бизнес-операции  | 
| Signature | string   | Подпись события  | 
| WorkerAdminName | string | Имя администратора машины робота  | 
| Text        | string  | Произвольное описание, связанное с событием  | 
| EventType   | Enum?   | Классификация события. См. поле **Код** в Таблице 2 (ниже)  |
| IP        | string    | IP-адрес, связанный с событием  | 
| TenantId  | string    | Идентификатор тенанта, в котором произошло событие  | 
| EntityData | string   | Расширенная информация о сущности, связанной с событием. См. свойство EntityId | 
| SendedAt   | DateTime | Дата отправки события в интеграционный end-point | 

Таблица 2 – Классификация событий Оркестратора
     
| Код | Наименование  | Описание     |  
| --- | ------------- | ------------ |   
| 1   | Info	       | Информационное |  
| 2   | Error         | Ошибка       |  
| 3   | SecurityIncident | Инцидент безопасности |  
| 4   | Correction    | Корректировка |  
     
**ВНИМАНИЕ!** Для ознакомления с перечнем событий Оркестратора см. [Приложение 3 - События Оркестратора](https://docs.primo-rpa.ru/primo-rpa/orchestrator/appendix/appendix3).

## End-point приема событий для интеграции с ArcSight

В качестве примера интеграционного end-point в поставку включена служба Primo.Orchestrator.ArcSight\*. Служба конвертирует события в формат ArcSight и сохраняет их в файлах в папке обмена. 

Служба Primo.Orchestrator.ArcSight не фильтрует события, в файлах обмена сохраняются все принятые события Оркестратора.

События записываются в файл по мере достижения максимального количества строк (настраивается в конфигурационном файле службы Primo.Orchestrator.ArcSight). Потом события записываются в следующий файл и так далее. 

При достижении максимального количества файлов в папке обмена старые файлы удаляются.

Механизм загрузки событий в ArcSight должен быть согласован с настройками Primo.Orchestrator.ArcSight, чтобы успеть загрузить события в ArcSight до их удаления. 

В качестве **end-point авторизации** при настройке LogEventsWebhook необходимо использовать адрес Оркестратора: https://{IP}:44392/api/Account.

В качестве **end-point приема событий** при настройке LogEventsWebhook необходимо использовать адрес Primo.Orchestrator.ArcSight: https://{IP}:44444/api/OrchEvents.
  
Ниже приведен пример содержимого файла ArcSight-2022052220.txt из папки обмена:
```
May 22 15:33:32 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|2001|Login|10|entityid='agent, tenantId=' entitydata='' ip=::ffff:192.168.1.159 operationkey= userid= workeradminname= id=ca73d6b2-5286-44fd-8ada-ff5c155d96c6
May 22 15:33:43 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|504|RobotStartStarted|10|entityid='87' entitydata='' ip=::ffff:192.168.1.159 operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid=admin workeradminname= id=26143b8f-a5bd-438b-9d7c-cc04753879f1
May 22 15:33:43 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|40006|AgentEnabledKeepRDPSession|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=0da49a5d-b333-4b6c-89e7-980ae7c461fa
May 22 15:33:46 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|40006|AgentEnabledKeepRDPSession|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=2046ab20-3529-4f21-98cd-b9a88e0f05e0
May 22 15:33:49 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|8001|AgentStartRobotTrackingStart|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=c4f0715e-7b3f-4d43-a21a-49583c58dbe6
May 22 15:33:49 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|415|ProjectDownloaded|10|entityid='1' entitydata='' ip=::ffff:192.168.1.159 operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid=agent workeradminname= id=4721b6ec-165c-4fb7-9cd2-9d308f6c4069
May 22 15:33:49 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|8010|AgentStartRobotTrackingDownloadProjectArch|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=22634d3e-ecc9-4e55-9e26-0f48fb67bbf3
May 22 15:33:49 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|8011|AgentStartRobotTrackingSaveProjectArch|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=897fad92-c9e9-4a44-b8f5-5ff10fddfb75
May 22 15:33:50 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|8021|AgentStartRobotTrackingGenerateRunScript|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=ab7f0532-faff-444d-a801-46dc69c622e9
May 22 15:33:51 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|8022|AgentStartRobotTrackingCreateTaskToStartRobot|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=a798956b-abc7-43bc-a710-a0815cb4377b
May 22 15:33:53 host CEF:0|Primo|Orchestrator.ArcSight|1.0.0.0|8040|AgentStartRobotWaitExecuteWorkflow|10|entityid='87' entitydata='' ip= operationkey=8a8224e3-43eb-4611-bbe0-4a7eedffa88a userid= workeradminname= id=478b2ebd-32bb-420e-9923-f5679b73136c
```

>\**Требования к сервису могут быть уточнены по результатам тестирования Заказчиком работы интеграции*.\
> **ССЫЛКА НА ДОКУ ПО УСТАНОВКЕ ArcSight в винде и Линуксе**
