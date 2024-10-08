# События

Все события, которые фиксируются в Primo RPA AI Server, приведены в таблице ниже. Список событий может измениться в следующих версиях Primo RPA AI Server.

### Запрос на извлечение данных (инференс)

Данный запрос отправляет робот, когда выполняет RPA-проект с элементом [Создать запрос](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/ai_server/createrequest). Запрос подразумевает обработку одного изображения с целью извлечь из него данные.

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 100   | InferenceRequestAccepted                  | Запрос на извлечение данных из изображения принят сервером в обработку |
| 101   | InferenceRequestSentForProcessingSuccess  | Запрос на извлечение данных из изображения успешно отправлен на целевую машину для обработки |
| 102   | InferenceRequestSentForProcessingError    | Отправка запроса на целевую машину завершилась ошибкой   |
| 103   | InferenceRequestNoAgent                   | Не найден агент, на котором запущен процесс инференса с типом модели, который указан в запросе на извлечение данных |
| 104   | InferenceRequestStartPipeline             | Старт конвейера запуска обработки запроса на инференс |
| 105   | InferenceRequestDownloadImgFileSuccess    | Успешно завершен этап загрузки на целевую машину файла изображения из запроса |
| 106   | InferenceRequestDownloadImgFileError      | Этап загрузки на целевую машину файла изображения завершен ошибкой |
| 107   | InferenceRequestDownloadMarkingFileSuccess | Успешно завершен этап загрузки на целевую машину схемы разметки |
| 108   | InferenceRequestDownloadMarkingFileError  | Этап загрузки на целевую машину схемы разметки завершен ошибкой |
| 109   | InferenceRequestProcessedSuccess          | Запрос на извлечение данных из изображения обработан успешно |
| 110   | InferenceRequestProcessedError            | Обработка запроса на извлечение данных из изображения завершилась ошибкой |
| 111   | InferenceRequestResultTransferred         | Извлеченные из изображения данные получены сервером  |
| 112   | InferenceRequestNoLicensedAgent           | Не найден лицензированный агент с указанным типом модели для обработки запроса. При данной ошибке необходимо обеспечить подходящего агента лицензией |


### Процесс инференса

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 200   | InferenceProcessCreated                   | Процесс инференса создан          |
| 201   | InferenceProcessRemoved                   | Процесс инференса удален          |
| 202   | InferenceProcessDisabled                  | Процесс инференса выключен        |
| 203   | InferenceProcessEnabled                   | Процесс инференса включен         |
| 204   | InferenceProcessStarted                   | Процесс инференса ожидает запуск |
| 205   | InferenceProcessStoped                    | Процесс инференса ожидает остановку |
| 206   | InferenceProcessSentToLaunch              | Процесс инференса запускается     |
| 207   | InferenceProcessSentToStop                | Процесс инференса останавливается |
| 208   | InferenceProcessStartingError             | Запуск процесса инференс завершился ошибкой |
| 209   | InferenceProcessStoppingError             | Остановка процесса инференса завершилась ошибкой |


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
| 401   | AgentUpdated                              | Целевая машина изменена           |
| 402   | AgentRemoved                              | Целевая машина удалена            |
| 403   | AgentDisabled                             | Целевая машина выключена          | 
| 404   | AgentEnabled                              | Целевая машина включена           | 
| 405   | AgentAutoDisabled                         | Целевая машина автоматически выключена из-за превышения времени недоступности. Максимальное время недоступности указывается в настройках конфигурационного файла (**Agents** > **AutoDisableUnavailablePeriod**) | 

### Скрипт

**Примечание**. В текущей версии сервиса скрипты не используются.

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 500   | ScriptCreated                             | Скрипт создан                     | 
| 501   | ScriptUpdated                             | Скрипт изменен                    | 
| 502   | ScriptRemoved                             | Скрипт удален                     | 


### Лицензия

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 601   | LicenseAdded                              | Лицензия добавлена                | 
| 602   | LicenseDeleted                            | Лицензия удалена. **Примечание:** в текущей версии нет функции удаления лицензии | 
| 603   | LicenseDownloaded                         | Лицензия скачана                  | 
| 604   | LicenseRevoked                            | Лицензия отозвана. **Примечание:** в текущей версии нет функции отзыва лицензии | 
| 605   | LicenseRevokeReplaced                     | Отозванная лицензия заменена. **Примечание:** в текущей версии нет функции замены отозванной | 
| 606   | LicenseRequested                          | Запрос на лицензию создан         | 
| 607   | LicenseReplaceRequested                   | Запрос на замену лицензии создан. **Примечание:** в текущей версии нет функции запроса замены лицензии | 
| 608   | LicenseToTenantAdded                      | Лицензия выдана на тенант         | 
| 609   | LicenseDeactivated                        | Лицензия деактивирована           | 
| 610   | LicenseActivated                          | Лицензия, которая ранее была деактивирована, вновь активирована | 

### Авторизация

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 2001  | Login                                     | Пользователь авторизовался в сервисе | 
| 2002  | LoginUserNotExist                         | Пользователь не существует        | 
| 2003  | LoginUserLocked                           | Попытка входа заблокированного пользователя. При попытке входа такой пользователь увидит уведомление `Ошибка аутентификации` | 
| 2004  | LoginUserUnauthorized                     | Ошибка авторизации | 
| 2005  | LoginUserUnauthorizedAD                   | Пользователь не авторизован в Active Directory (AD). **Примечание**: в текущей версии AD-пользователи не используются |  
| 2006  | LoginUserNoRightsGroupAD                  | Роль пользователя не имеет привязки к AD-группе. **Примечание**: в текущей версии AD-пользователи не используются |  
| 2007  | LogOut                                    | Пользователь вышел из сервиса     |  
| 2008  | LoginUserExpired                          | Срок действия учетной записи с текущим паролем истек |  


### Проект

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 3000  | ProjectCreated                            | Проект создан                     |  
| 3001  | ProjectUpdated                            | Проект изменен                    |  
| 3002  | ProjectRemoved                            | Проект удален                     |  


### Данные

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 4000  | ProjectDataImgCreated                     | Файлы изображений добавлены в проект или извлечены из загруженного архива    |  
| 4001  | ProjectDataImgUpdated                     | Файлы изображений изменены              |  
| 4002  | ProjectDataImgRemoved                     | Файлы изображений удалены               |  
| 4003  | ProjectDataImgArchiveUploaded             | Архив с изображениями загружен          |  
| 4004  | ProjectDataImgCreateError                 | Добавление файлов изображений завершилось ошибкой |  


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
| 6003  | MarkingFieldTypesUpdated                  | Параметры полей схемы разметки изменены на странице "Инференс > Поля"/"Документы"  |   
| 6004  | MarkingFieldColumnsUpdated                | Настройки табличных полей схемы разметки изменены на странице "Поля" |   



### Роль

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 8000  | RoleCreated                               | Роль создана                      |  
| 8001  | RoleUpdated                               | Роль изменена                     |  
| 8002  | RoleRemoved                               | Роль удалена                      |       
| 8003  | RoleAssignAdGroups                        | Роль привязана к AD-группе. **Примечание:** в текущей версии AD-группы не используются |    
| 8004  | RoleAssignPermissions                     | Роли назначены разрешения         |    


### Пользователь

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 9000  | UserCreated                               | Пользователь создан               |    
| 9001  | UserUpdated                               | Пользователь изменен              |  
| 9002  | UserRemoved                               | Пользователь удален               |     
| 9003  | UserRolesAssigned                         | Пользователю назначены роли       |     
| 9004  | UserPasswordChanged                       | Пароль пользователя изменен       |   
| 9005  | UserEnabled                               | Пользователь разблокирован        |  
| 9006  | UserDisabled                              | Пользователь заблокирован. Вход заблокированного пользователя будет временно ограничен |  


### Шаблон модели

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 10000 | ModelTemplateCreated                      | Шаблон модели создан              |  
| 10001 | ModelTemplateUpdated                      | Шаблон модели отредактирован      |  
| 10002 | ModelTemplateRemoved                      | Шаблон модели удален              |  

### Разметка данных

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 11000 | MarkingCreateOrEdit                       | Изображение размечено или переразмечено  |  
| 11001 | MarkingRemoved                            | Разметка изображения удалена             |  
| 11002 | MarkingMovedToDataSet                     | Разметка изображения добавлена в датасет |      

### Датасет

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 12000 | DataSetCreated                            | Датасет создан                    |   
| 12001 | DataSetUpdated                            | Датасет изменен                   |   
| 12002 | DataSetRemoved                            | Датасет удален                    |   
| 12003 | DataSetArchivateStarted                   | Запущена архивация датасета       |   
| 12004 | DataSetArchivateCompletedSuccess          | Архивирование датасета успешно завершено |   
| 12005 | DataSetArchivateCompletedError            | Архивирование датасета завершилось ошибкой |
| 12006 | DataSetArchivateProgress1                 | Этап подготовки данных изображения датасета успешно завершен |
| 12007 | DataSetArchivateProgress2                 | Этап добавления в архив данных изображения датасета успешно завершен |
| 12008 | DataSetArchivateCompletedTimeout          | Не удается за отведенное в конфигурации время сформировать архив датасета вследствие ошибок или размеров датасета. Параметры конфигурации сервиса: **DateSet** > **ArchivateTimeout** |
| 12009 | DataSetArchiveUploaded                    | Архив с датасетом загружен для обработки        |
| 12010 | DataSetArchiveImportSucceed               | Импорт датасета из загруженного архива выполнен успешно  |
| 12011 | DataSetArchiveImportFailed                | Импорт датасета из загруженного архива завершился ошибкой |


### Тип модели

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 13000 | ModelTypeCreated                          | Тип модели создан                 |
| 13001 | ModelTypeUpdated                          | Тип модели изменен                |
| 13002 | ModelTypeRemoved                          | Тип модели удален                 |


### Модель

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 14000 | ModelCreated                              | Модель создана                    |
| 14001 | ModelUpdated                              | Модель изменена                   |
| 14002 | ModelRemoved                              | Модель удалена                    |
| 14003 | ModelDownloadSuccess                      | Модель загружена успешно          |
| 14004 | ModelDownloadError                        | Загрузка модели завершилась ошибкой |


### Процесс обучения

|  Код  | Событие                                   | Описание                          |
| ----- | ----------------------------------------- | --------------------------------- |
| 15000 | TrainProcessCreated                       | Процесс обучения создан           |
| 15001 | TrainProcessRemoved                       | Процесс обучения удален           |
| 15002 | TrainProcessDisabled                      | Процесс обучения выключен. Выключенный процесс становится недоступным для запуска и остановки |
| 15003 | TrainProcessEnabled                       | Процесс обучения, который ранее был выключен, вновь включен |
| 15004 | TrainProcessSendToStart                   | Процесс обучения отправлен на целевую машину для запуска  |
| 15005 | TrainProcessStarted                       | Процесс обучения готов к запуску  |
| 15006 | TrainProcessSendToStop                    | Процесс обучения останавливается  |
| 15007 | TrainProcessStopedSuccess                 | Процесс обучения успешно остановлен |
| 15008 | TrainProcessStopedError                   | Остановка процесса обучения завершилась ошибкой (например, не хватает прав для остановки процесса в ОС целевой машины) |
| 15100 | TrainProcessStartPipeline                 | Старт конвейера запуска процесса обучения |
| 15101 | TrainProcessEmergencyShutdown             | При запуске агента было обнаружено, что процесс обучения аварийно завершен и не выполняется  |
| 15200 | TrainProcessStartFileStoragePrepareSuccess | Файловое хранилище успешно подготовлено |  
| 15201 | TrainProcessStartFileStoragePrepareError  | Подготовка файлового хранилища завершилась ошибкой (например, не хватает прав для создания папки с данными процесса обучения на целевой машине) |
| 15300 | TrainProcessStartDownloadScriptSuccess    | Файл скрипта скачан. **Примечание:** в текущей версии пользовательские скрипты не поддерживаются |
| 15301 | TrainProcessStartDownloadScriptError      | Скачивание файла скрипта завершилось ошибкой. **Примечание:** в текущей версии пользовательские скрипты не поддерживаются |
| 15400 | TrainProcessStartDownloadModelTemplateSuccess      | Шаблон модели загружен успешно  |
| 15401 | TrainProcessStartDownloadModelTemplateError        | Загрузка шаблона модели завершилась ошибкой |
| 15402 | TrainProcessStartUnzipModelTemplateSuccess         | Распаковка шаблона модели успешно запущена |
| 15403 | TrainProcessStartUnzipModelTemplateError           | Распаковка шаблона модели завершилась ошибкой |
| 15500 | TrainProcessStartDownloadModelSuccess              | Загрузка модели успешно запущена |
| 15501 | TrainProcessStartDownloadModelError                | Загрузка модели завершилось ошибкой |
| 15502 | TrainProcessStartUnzipModelSuccess                 | Распаковка архива модели успешно запущена |
| 15503 | TrainProcessStartUnzipModelError                   | Распаковка архива модели завершилась ошибкой |
| 15600 | TrainProcessStartDownloadDataSetSuccess            | Загрузка датасета для обучения успешно запущена |
| 15601 | TrainProcessStartDownloadDataSetError              | Загрузка датасета для обучения завершилась ошибкой |
| 15602 | TrainProcessStartUnzipDataSetSuccess               | Распаковка датасета успешно запущена |
| 15603 | TrainProcessStartUnzipDataSetError                 | Распаковка датасета завершилась ошибкой |
| 15620 | TrainProcessStartDownloadTestDataSetSuccess        | Загрузка архива тестового датасета успешно запущена |
| 15621 | TrainProcessStartDownloadTestDataSetError          | Загрузка архива тестового датасета завершилась ошибкой |
| 15622 | TrainProcessStartDownloadUnzipTestDataSetSuccess   | Распаковка архива тестового датасета успешно запущена |
| 15623 | TrainProcessStartDownloadUnzipTestDataSetError     | Распаковка архива тестового датасета завершилась ошибкой |
| 15700 | TrainProcessStartCompletedSuccess                  | Запуск процесса обучения завершен успешно |
| 15701 | TrainProcessStartCompletedError                    | Запуск процесса обучения завершен с ошибкой |
| 15800 | TrainProcessCompletedSuccess                       | Процесс обучения успешно завершен. Результатом обучения является обученная модель |
| 15801 | TrainProcessCompletedError                         | Процесс обучения завершился ошибкой |
| 15800 | TrainProcessTimeout                                | Процесс обучения завершился с ошибкой таймаута. Например, при нехватке прав или библиотек аварийно завершился IDP-процесс |
| 15900 | TrainProcessMetricsReceived                        | Получены метрики процесса обучения |


### Шаблон обучения

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 16000 | TrainProcessTemplateCreated                       | Шаблон обучения создан            |
| 16001 | TrainProcessTemplateUpdated                       | Шаблон обучения обновлен          |
| 16002 | TrainProcessTemplateRemoved                       | Шаблон обучения удален            |

### Пайплан

**Примечание**. В текущей версии сервиса пайплайны не используются.

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 17000 | PipelineCreated                                   | Пайплан создан                    |
| 17001 | PipelineUpdated                                   | Пайплан обновлен                  |
| 17002 | PipelineRemoved                                   | Пайплан удален                    |


### Процесс инференса 

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 18100 | InferenceProcessStartPipeline                     | Старт конвейера запуска процесса инференса  |
| 18101 | InferenceProcessEmergencyShutdown                 | При запуске агента было обнаружено, что процесс инференса аварийно завершен и не выполняется |
| 18200 | InferenceProcessStartFileStoragePrepareSuccess    | Файловое хранилище успешно подготовлено |
| 18201 | InferenceProcessStartFileStoragePrepareError      | Подготовка файлового хранилища завершилась ошибкой. Например, не хватает прав для создания папки с данными процесса обучения на целевой машине |
| 18300 | InferenceProcessStartDownloadScriptSuccess        | Скачивание файла скрипта завершилось успешно. **Примечание:** в текущей версии пользовательские скрипты не поддерживаются |
| 18301 | InferenceProcessStartDownloadScriptError          | Скачивание файла скрипта завершилось ошибкой. **Примечание:** в текущей версии пользовательские скрипты не поддерживаются |
| 18500 | InferenceProcessStartDownloadModelSuccess         | Скачивание модели завершилось успешно  |
| 18501 | InferenceProcessStartDownloadModelError           | Скачивание модели завершилось ошибкой |
| 18502 | InferenceProcessStartUnzipModelSuccess            | Распаковка архива модели завершилась успешно |
| 18503 | InferenceProcessStartUnzipModelError              | Распаковка архива модели завершилась ошибкой |
| 18600 | InferenceProcessStartDownloadMarkingSchemeSuccess | Скачивание схемы разметки завершилась успешно |
| 18601 | InferenceProcessStartDownloadMarkingSchemeError   | Скачивание схемы разметки завершилось ошибкой |
| 18700 | InferenceTestProcessStartDownloadDataSetSuccess   | Скачивание тестового датасета завершилась успешно (тестовый процесс инференса) |
| 18701 | InferenceTestProcessStartDownloadDataSetError     | Скачивание тестового датасета завершилось ошибкой |
| 18702 | InferenceTestProcessStartUnzipDataSetSuccess      | Распаковка тестового датасета завершилась успешно |
| 18703 | InferenceTestProcessStartUnzipDataSetError        | Распаковка тестового датасета завершилось ошибкой |
| 18800 | InferenceProcessStartCompletedSuccess             | Процесс инференса успешно запущен             |
| 18801 | InferenceProcessStartCompletedError               | Запуск процесса инференса завершился ошибкой  |
| 18900 | InferenceTestProcessTransferEvaluationResultSuccess | Показатели оценки процесса тестового инференс получены сервером |
| 18920 | InferenceTestProcessTransferBboxSuccess           | Координаты полей тестового инференс получены сервером |
| 18940 | InferenceTestProcessCompletedSuccess              | Тестовый процесс инференса завершен успешно   |
| 18960 | InferenceTestProcessCompletedError                | Тестовый процесс инференса завершился ошибкой |


### Данные журнала агента

| Код   | Событие                                           | Описание                          |
| ----- | ------------------------------------------------- | --------------------------------- |
| 19000 | AgentLogDataReceived                              | Данные из журнала агента получены сервером |




