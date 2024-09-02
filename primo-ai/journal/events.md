# События

Все события, которые фиксируются в Primo RPA AI Server, приведены в таблице ниже.

Список событий может измениться в следующих версиях Primo RPA AI Server.

### Запрос на инференс

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 100   | InferenceRequestAccepted                  |                                   |
| 101   | InferenceRequestSentForProcessingSuccess  |                                   |
| 102   | InferenceRequestSentForProcessingError    |                                   |
| 103   | InferenceRequestNoAgent                   |                                   |
| 104   | InferenceRequestStartPipeline             |                                   |
| 105   | InferenceRequestDownloadImgFileSuccess    |                                   |
| 106   | InferenceRequestDownloadImgFileError      |                                   |
| 107   | InferenceRequestDownloadMarkingFileSuccess |                                  |
| 108   | InferenceRequestDownloadMarkingFileError  |                                   |
| 109   | InferenceRequestProcessedSuccess          |                                   |
| 110   | InferenceRequestProcessedError            |                                   |
| 111   | InferenceRequestResultTransferred         |                                   |
| 112   | InferenceRequestNoLicensedAgent           |                                   |

### Процесс инференса

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 200   | InferenceProcessCreated                   | Процесс инференса создан          |
| 201   | InferenceProcessRemoved                   | Процесс инференса удален          |
| 202   | InferenceProcessDisabled                  | Процесс инференса выключен        |
| 203   | InferenceProcessEnabled                   | Процесс инференса включен         |
| 204   | InferenceProcessStarted                   | Процесс инференса **(запущен?)** |
| 205   | InferenceProcessStoped                    | Процесс инференса остановлен      |
| 206   | InferenceProcessSentToLaunch              | Процесс инференса **отправлен на запуск??** |
| 207   | InferenceProcessSentToStop                | Процесс инференса **отправлен на остановку?** |
| 208   | InferenceProcessStartingError             | **Запуск процесса инференса завершился ошибкой?** |
| 209   | InferenceProcessStoppingError             | **Остановка процесса инференса завершилась ошибкой?** |


### Шаблон процесса инференса

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 300   | InferenceProcessTemplateCreated           | Шаблон процесса инференса создан  |
| 301   | InferenceProcessTemplateUpdated           | Шаблон процесса инференса изменен |
| 302   | InferenceProcessTemplateRemoved           | Шаблон процесса инференса удален  |


### Целевая машина

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 400   | AgentCreated                              | Целевая машина создана            |
| 401   | AgentUpdated                              | Целевая машина обновлена          |
| 402   | AgentRemoved                              | Целевая машина удалена            |
| 403   | AgentDisabled                             | Целевая машина выключена          | 
| 404   | AgentEnabled                              | Целевая машина включена           | 
| 405   | AgentAutoDisabled                         | Целевая машина автоматически выключена (**ТРЕБУЕТ ПОЯСНЕНИЙ**)  | 

### Скрипт

В текущей версии сервиса скрипты не используются.

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 500   | ScriptCreated                             | Скрипт создан                     | 
| 501   | ScriptUpdated                             | Скрипт изменен                    | 
| 502   | ScriptRemoved                             | Скрипт удален                     | 


### Лицензия

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 601   | LicenseAdded                              | Сгенерирован запрос лицензии  (**НУЖНО ПОЯСНЕНИЕ**) | 
| 602   | LicenseDeleted                            | Лицензия (???)                    | 
| 603   | LicenseDownloaded                         | Лицензия загружна в сервис        | 
| 604   | LicenseRevoked                            | Лицензия отозвана                 | 
| 605   | LicenseRevokeReplaced                     | Отозванная лицензия заменена? (**НУЖНО ПОЯСНЕНИЕ**) | 
| 606   | LicenseRequested                          |                                   | 
| 607   | LicenseReplaceRequested                   |                                   | 
| 608   | LicenseToTenantAdded                      |                                   | 
| 609   | LicenseDeactivated                        |                                   | 
| 610   | LicenseActivated                          |                                   | 

### Авторизация

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 2001  | Login                                     | Пользователь авторизовался в сервисе | 
| 2002  | LoginUserNotExist                         | Указанный логин пользователя не существует (?) | 
| 2003  | LoginUserLocked                           |                                   | 
| 2004  | LoginUserUnauthorized                     |                                   | 
| 2005  | LoginUserUnauthorizedAD                   |                                   |  
| 2006  | LoginUserNoRightsGroupAD                  |                                   |  
| 2007  | LogOut                                    | Пользователь вышел из сервиса     |  
| 2008  | LoginUserExpired                          |                                   |  


### Проект

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 3000  | ProjectCreated                            | Проект создан                     |  
| 3001  | ProjectUpdated                            | Проект изменен                    |  
| 3002  | ProjectRemoved                            | Проект удален                     |  


### Данные

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 4000  | ProjectDataImgCreated                     |                                   |  
| 4001  | ProjectDataImgUpdated                     |                                   |  
| 4002  | ProjectDataImgRemoved                     |                                   |  
| 4003  | ProjectDataImgArchiveUploaded             |                                   |  
| 4004  | ProjectDataImgCreateError                 |                                   |  


### Схема разметки

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 5000  | MarkingSchemeCreated                      | Схема разметки создана            |  
| 5001  | MarkingSchemeUpdated                      | Схема разметки изменена           |  
| 5002  | MarkingSchemeRemoved                      | Схема разметки удалена            |  

### Поля схемы разметки

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 6000  | MarkingFieldCreated                       | Поле создано                      |  
| 6001  | MarkingFieldUpdated                       | Поле изменено                     |   
| 6002  | MarkingFieldRemoved                       | Поле удалено                      |   
| 6003  | MarkingFieldTypesUpdated                  |                                   |   
| 6004  | MarkingFieldColumnsUpdated                |                                   |   


### Папка (что за папка имеется в виду?)

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 7000  | FolderCreated                             |                                   |   
| 7001  | FolderUpdated                             |                                   |   
| 7002  | FolderRemoved                             |                                   |  
| 7003  | FolderResubordination                     |                                   |  
| 7004  | FolderMoveObjects                         |                                   |  
| 7005  | FolderGrantUserFolders                    |                                   |  
| 7006  | FolderGrantFolderUsers                    |                                   |  


### Роль

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 8000  | RoleCreated                               | Роль создана                      |  
| 8001  | RoleUpdated                               | Роль изменена                     |  
| 8002  | RoleRemoved                               | Роль удалена                      |       
| 8003  | RoleAssignAdGroups                        | Роль привязана к AD-группе (в текущей версии AD-группы не используются) |    
| 8004  | RoleAssignPermissions                     | Роли назначены разрешения         |    


### Пользователь

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 9000  | UserCreated                               | Пользователь создан               |    
| 9001  | UserUpdated                               | Пользователь изменен              |  
| 9002  | UserRemoved                               | Пользователь удален               |     
| 9003  | UserRolesAssigned                         | **Пользователю назначены роли**  |     
| 9004  | UserPasswordChanged                       | Пароль пользователя изменен       |   
| 9005  | UserEnabled                               | Пользователь **разблокирован?**   |  
| 9006  | UserDisabled                              | Пользователь **заблокирован?**    |  


### Шаблон модели

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 10000 | ModelTemplateCreated                      |                                   |  
| 10001 | ModelTemplateUpdated                      |                                   |  
| 10002 | ModelTemplateRemoved                      |                                   |  

### Разметка

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 11000 | MarkingCreateOrEdit                       |                                   |  
| 11001 | MarkingRemoved                            |                                   |  
| 11002 | MarkingMovedToDataSet                     |                                   |      

### Датасет

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 12000 | DataSetCreated                            |                                   |   
| 12001 | DataSetUpdated                            |                                   |   
| 12002 | DataSetRemoved                            |                                   |   
| 12003 | DataSetArchivateStarted                   |                                   |   
| 12004 | DataSetArchivateCompletedSuccess          |                                   |   
| 12005 | DataSetArchivateCompletedError            |                                   |
| 12006 | DataSetArchivateProgress1                 |                                   |
| 12007 | DataSetArchivateProgress2                 |                                   |
| 12008 | DataSetArchivateCompletedTimeout          |                                   |
| 12009 | DataSetArchiveUploaded                    |                                   |
| 12010 | DataSetArchiveImportSucceed               |                                   |
| 12011 | DataSetArchiveImportFailed                |                                   |


### Тип модели

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 13000 | ModelTypeCreated                          |                                   |
| 13001 | ModelTypeUpdated                          |                                   |
| 13002 | ModelTypeRemoved                          |                                   |
| 14000 | ModelCreated                              |                                   |
| 14001 | ModelUpdated                              |                                   |
| 14002 | ModelRemoved                              |                                   |
| 14003 | ModelDownloadSuccess                      |                                   |
| 14004 | ModelDownloadError                        |                                   |


### Процесс обучения

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 15000 | TrainProcessCreated                       |                                   |
| 15001 | TrainProcessRemoved                       |                                   |
| 15002 | TrainProcessDisabled                      |                                   |
| 15003 | TrainProcessEnabled                       |                                   |
| 15004 | TrainProcessSendToStart                   |                                   |
| 15005 | TrainProcessStarted                       |                                   |
| 15006 | TrainProcessSendToStop                    |                                   |
| 15007 | TrainProcessStopedSuccess                 |                                   |
| 15008 | TrainProcessStopedError                   |                                   |
| 15100 | TrainProcessStartPipeline                 |                                   |
| 15101 | TrainProcessEmergencyShutdown             |                                   |
| 15200 | TrainProcessStartFileStoragePrepareSuccess |                                  |  
| 15201 | TrainProcessStartFileStoragePrepareError  |                                   |
| 15300 | TrainProcessStartDownloadScriptSuccess    |   |
| 15301 | TrainProcessStartDownloadScriptError      |   |
| 15400 | TrainProcessStartDownloadModelTemplateSuccess      |  |
| 15401 | TrainProcessStartDownloadModelTemplateError        |  |
| 15402 | TrainProcessStartUnzipModelTemplateSuccess         |  |
| 15403 | TrainProcessStartUnzipModelTemplateError           |  |
| 15500 | TrainProcessStartDownloadModelSuccess              |  |
| 15501 | TrainProcessStartDownloadModelError                |  |
| 15502 | TrainProcessStartUnzipModelSuccess                 |  |
| 15503 | TrainProcessStartUnzipModelError                   |  |
| 15600 | TrainProcessStartDownloadDataSetSuccess            |  |
| 15601 | TrainProcessStartDownloadDataSetError              |  |
| 15602 | TrainProcessStartUnzipDataSetSuccess               |  |
| 15603 | TrainProcessStartUnzipDataSetError                 |  |
| 15620 | TrainProcessStartDownloadTestDataSetSuccess        |  |
| 15621 | TrainProcessStartDownloadTestDataSetError          |  |
| 15622 | TrainProcessStartDownloadUnzipTestDataSetSuccess   |  |
| 15623 | TrainProcessStartDownloadUnzipTestDataSetError     |  |
| 15700 | TrainProcessStartCompletedSuccess                  |  |
| 15701 | TrainProcessStartCompletedError                    |  |
| 15800 | TrainProcessCompletedSuccess                       |  |
| 15801 | TrainProcessCompletedError                         |  |
| 15800 | TrainProcessTimeout                                |  |
| 15900 | TrainProcessMetricsReceived                        |  |
 

### Шаблон обучения

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 16000 | TrainProcessTemplateCreated                       | Шаблон обучения создан |
| 16001 | TrainProcessTemplateUpdated                       | Шаблон обучения обновлен |
| 16002 | TrainProcessTemplateRemoved                       | Шаблон обучения удален |

### Пайплан

В текущей версии сервиса пайплайны не используются.

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 17000 | PipelineCreated                                   | Пайплан создан |
| 17001 | PipelineUpdated                                   | Пайплан обновлен |
| 17002 | PipelineRemoved                                   | Пайплан удален |


### Процесс инференса - ?

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 18100 | InferenceProcessStartPipeline                     |  |
| 18101 | InferenceProcessEmergencyShutdown                 |  |
| 18200 | InferenceProcessStartFileStoragePrepareSuccess    |  |
| 18201 | InferenceProcessStartFileStoragePrepareError      |  |
| 18300 | InferenceProcessStartDownloadScriptSuccess        |  |
| 18301 | InferenceProcessStartDownloadScriptError          |  |
| 18500 | InferenceProcessStartDownloadModelSuccess         |  |
| 18501 | InferenceProcessStartDownloadModelError           |  |
| 18502 | InferenceProcessStartUnzipModelSuccess            |  |
| 18503 | InferenceProcessStartUnzipModelError              |  |
| 18600 | InferenceProcessStartDownloadMarkingSchemeSuccess |  |
| 18601 | InferenceProcessStartDownloadMarkingSchemeError   |  |
| 18700 | InferenceTestProcessStartDownloadDataSetSuccess   |  |
| 18701 | InferenceTestProcessStartDownloadDataSetError     |  |
| 18702 | InferenceTestProcessStartUnzipDataSetSuccess      |  |
| 18703 | InferenceTestProcessStartUnzipDataSetError        |  |
| 18800 | InferenceProcessStartCompletedSuccess             |  |
| 18801 | InferenceProcessStartCompletedError               |  |
| 18900 | InferenceTestProcessTransferEvaluationResultSuccess |  |
| 18920 | InferenceTestProcessTransferBboxSuccess           |  |
| 18940 | InferenceTestProcessCompletedSuccess              |  |
| 18960 | InferenceTestProcessCompletedError                |  |


### Данные журнала агента

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 19000 | AgentLogDataReceived                              |  |




