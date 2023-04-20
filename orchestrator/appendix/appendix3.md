# Приложение 3 - События Оркестратора

Таблица 1. – Перечень событий Оркестратора.

| № п/п    | Код   | Наименование                                     | Описание                                        |
| -------- | ----- | ------------------------------------------------ | ----------------------------------------------- |
| 1.       | 1     | OrchestratorStarted                              | Оркестратор стартовал        |
| 2.       | 101   | UserCreated                                      | Пользователь создан          |
| 3.       | 102   | AdUserCreated                                    | Пользователь AD зарегистрирован  |
| 4.       | 103   | UserChanged                                      | Пользователь изменен         |
| 5.       | 104   | UserDisabled                                     | Пользователь отключен        |
| 6.       | 105   | UserRolesAssigned                                | Пользователю назначены роли  |
| 7.       | 106   | UserEnabled                                      | Пользователь включен     |
| 8.       | 107   | UserDeleted                                      | Пользователь удален      |
| 9.       | 108   | UserPasswordChanged                              | Пользователь изменил свой пароль  |
| 10.      | 201   | RoleCreated                                      | Роль создана                      |
| 11.      | 202   | RoleChanged                                      | Роль изменена                     |
| 12.      | 203   | RoleDeleted                                      | Роль удалена                      |
| 13.      | 204   | RolePermissionsAssigned                          | Роли назначены права              |
| 14.      | 301   | WorkerCreated                                    | Машина зарегистрирована           |
| 15.      | 302   | WorkerChanged                                    | Машина изменена                   |
| 16.      | 303   | WorkerDisabled                                   | Машина выведена из эксплуатации   |
| 17.      | 304   | WorkerRebootStarted                              | Перезагрузка машины запущена      |
| 18.      | 305   | WorkerRebootCompleted                            | Перезагрузка машины завершена     |
| 19.      | 306   | WorkerTestAvailable                              | Машина доступна                   |
| 20.      | 307   | WorkerTestNotAvailable                           | Машина недоступна                 |
| 21.      | 308   | WorkerIpAddressSended                            | Машина робота отправила свой IP Оркестратору |
| 22.      | 401   | ProjectCreated                                   | Проект создан                     |
| 23.      | 402   | ProjectChanged                                   | Проект изменен                    |
| 24.      | 403   | ProjectDisabled                                  | Проект выведен из эксплуатации    |
| 25.      | 404   | ProjectRun                                       | Проект запущен                    |
| 26.      | 405   | ProjectAddedRobot                                | К проекту добавлен робот          |
| 27.      | 406   | ProjectDeletedRobot                              | Из проекта удален робот           |
| 28.      | 407   | ProjectChangedRobotOrder                         | Изменение приоритета роботов проекта |
| 29.      | 408   | ProjectEnqueue                                   | Проект добавлен в очередь выполнения |
| 30.      | 409   | ProjectPeek                                      | Проект извлечен из очереди выполнения |            
| 31.      | 410   | ProjectReEnqueue                                 | Проект добавлен в очередь выполнения повторно |   
| 32.      | 411   | ProjectSwappedMainVersionUp                      | Проект назначен главной версией      |
| 33.      | 412   | ProjectSwappedMainVersionDown                    | Проект больше не является главной версией |
| 34.      | 413   | ProjectVersionCreated                            | Версия проекта создана |
| 35.      | 414   | ProjectDeletedFromQueue                          | Проект удален из очереди на выполнение |
| 36.      | 415   | ProjectDownloaded                                | Скачан архив проекта   |
| 37.      | 417   | ProjectVariablesChanged                          | Переменные проекта изменены |
| 38.      | 501   | RobotCreated                                     | Робот зарегистрирован       |
| 39.      | 502   | RobotDisabled                                    | Робот выведен из эксплуатации |
| 40.      | 503   | RobotDeployStarted                               | Развертывание робота запущено |
| 41.      | 504   | RobotStartStarted                                | Старт робота запущен          |
| 42.      | 505   | RobotStartCompleted                              | Старт робота завершен         |
| 43.      | 506   | RobotEraseStarted                                | Стирание робота запущено      |
| 44.      | 507   | RobotEraseCompleted                              | Стирание робота завершено     |
| 45.      | 508   | RobotProjectRun                                  | Проект на роботе запущен      |
| 46.      | 509   | RobotProjectStopped                              | Проект на роботе остановлен   |
| 47.      | 510   | RobotDeployCompleted                             | Развертывание робота завершено |
| 48.      | 511   | RobotStartError                                  | Ошибка при запуске робота      |
| 49.      | 512   | RobotProjectCompletedSuccess                     | Зафиксировано удачное завершение выполнения проекта роботом |
| 50.      | 513   | RobotProjectCompletedError                       | Зафиксировано неудачное завершение выполнения проекта роботом |
| 51.      | 514   | RobotHardKillStarted                             | Старт принудительной остановки робота |
| 52.      | 515   | RobotHardKillCompleted                           | Принудительная остановка робота завершена |           
| 53.      | 516   | RobotSoftKillStarted                             | Старт мягкой остановки робота         |
| 54.      | 517   | RobotSoftKillCompleted                           | Мягкая остановка робота завершена     |
| 55.      | 518   | RobotStartedFromAssignment                       | Робот запущен из задания     |
| 56.      | 601   | LicenseAdded                                     | Лицензия добавлена           |   
| 57.      | 602   | LicenseDeleted                                   | Лицензия удалена             |
| 58.      | 603   | LicenseDownloaded                                | Лицензия скачана             |
| 59.      | 604   | LicenseRevoked                                   | Лицензия отозвана            |
| 60.      | 605   | LicenseRevokeReplaced                            | Отозванная лицензия заменена |
| 61.      | 606   | LicenseRequested                                 | Создан запрос на новую лицензию |
| 62.      | 607   | LicenseReplaceRequested                          | Создан запрос на замен лицензии |
| 63.      | 608   | LicenseTakeAvailableRobotOk                      | Робот занял свободную лицензию  |
| 64.      | 609   | LicenseTakeAvailableRobotError                   | Ошибка занятия лицензии роботом |
| 65.      | 610   | LicenseRobotReleaseOk                            | Лицензия робота освобождена     |
| 66.      | 611   | LicenseRobotReleaseError                         | Ошибка освобождения лицензии робота |
| 67.      | 612   | LicenseToTenantAdded                             | Лицензия выдана на тенант       |
| 68.      | 613   | LicenseTakeAvailableStudioOk                     | Студия заняла свободную лицензию |
| 69.      | 614   | LicenseTakeAvailableStudioError                  | Ошибка занятия лицензии студией  |
| 70.      | 615   | LicenseStudioTimeoutRelease                      | Лицензия студии освобождена по таймауту |
| 71.      | 616   | LicenseRobotTimeoutRelease                       | Лицензия робота освобождена по таймауту |
| 72.      | 617   | LicenseTakeAvailableAttendedRobotOk              | Аттендед робот занял свободную лицензию |
| 73.      | 618   | LicenseTakeAvailableAttendedRobotError           | Ошибка занятия лицензии аттендед роботом |
| 74.      | 619   | LicenseAttendedRobotReleaseOk                    | Лицензия аттендед робота освобождена |
| 75.      | 620   | LicenseAttendedRobotReleaseError                 | Ошибка освобождения лицензии аттендед робота |
| 76.      | 701   | AssetCreated                                     | Ресурс создан                      |
| 77.      | 702   | AssetChanged                                     | Ресурс изменен                     |
| 78.      | 703   | AssetDeleted                                     | Ресурс удален                      |
| 79.      | 801   | DeployTemplateCreated                            | Шаблон развертывания создан        |
| 80.      | 802   | DeployTemplateChanged                            | Шаблон развертывания изменен       |          
| 81.      | 803   | DeployTemplateDisabled                           | Шаблон развертывания выведен из эксплуатации |
| 82.      | 1201  | RobotDistrUploaded                               | Дистрибутив робота загружен        |
| 83.      | 1202  | RobotDistrActivated                              | Дистрибутив робота активирован     |
| 84.      | 1203  | RobotDistrDeleted                                | Дистрибутив робота удален          |
| 85.      | 2001  | Login                                            | Пользователь авторизовался         |
| 86.      | 2002  | LoginUserNotExists                               | Пользователь не существует         |
| 87.      | 2003  | LoginUserLocked                                  | Пользователь заблокирован          |
| 88.      | 2004  | LoginUserUnauthorized                            | Ошибка авторизации                 |
| 89.      | 2005  | LoginUserUnauthorizedAD                          | Ошибка авторизации в AD            |
| 90.      | 2006  | LoginUserNoRightsGroupAD                         | Группа AD не имеет привязки к роли |
| 91.      | 2007  | LogOut                                           | Пользователь вышел из системы      |
| 92.      | 2008  | LoginUserExpired                                 | Срок действия учетной записи истек |
| 93.      | 3001  | ExchangeQueueCreated                             | Очередь обмена для роботов создана |
| 94.      | 3002  | ExchangeQueueChanged                             | Очередь обмена для роботов изменена |
| 95.      | 3003  | ExchangeQueueDeleted                             | Очередь обмена для роботов удалена  |
| 96.      | 3004  | ExchangeQueuePermissionsAssigned                 | Очередь обмена для роботов - назначены права |
| 97.      | 3005  | ExchangeQueueEnqueue                             | Очередь обмена для роботов - добавление значения |
| 98.      | 3006  | ExchangeQueuePeek                                | Очередь обмена для роботов - извлечение значения |
| 99.      | 3007  | ExchangeQueueReadedByKey                         | Очередь обмена для роботов - чтение значения по ключу |
| 100.     | 3008  | ExchangeQueueRemovedByKey                        | Очередь обмена для роботов - удаление значения по ключу |
| 101.     | 3009  | ExchangeQueueChangeStatusByKey                   | Очередь обмена для роботов - изменение статуса элемента по ключу |
| 102.     | 3011  | ExchangeQueueAddMetadataByKey                    | Очередь обмена для роботов - добавление метаданных к элементу по ключу |
| 103.     | 3012  | ExchangeQueueReadedItems                         | Очередь обмена для роботов - чтение элементов по фильтру |
| 104.     | 3013  | ExchangeQueueItemTagsAdded                       | Очередь обмена для роботов - добавление тегов к элементу |
| 105.     | 3014  | ExchangeQueueItemTagsDeleted                     | Очередь обмена для роботов - удаление тегов у элемента |
| 106.     | 3015  | ExchangeQueueAddTagsByKey                        | Очередь обмена для роботов - добавление тегов к элементу по ключу |
| 107.     | 3016  | ExchangeQueueEnqueueFromOrchestrator             | Очередь обмена для роботов - добавление элемента из оркестратора |
| 108.     | 3017  | ExchangeQueueItemChangedFromOrchestrator         | Очередь обмена для роботов - изменение элемента из оркестратора |
| 109.     | 3018  | ExchangeQueueItemDeletedFromOrchestrator         | Очередь обмена для роботов - удаление элемента из оркестратора |
| 110.     | 3019  | ExchangeQueueItemClonedFromOrchestrator          | Очередь обмена для роботов - клонирование элемента из оркестратора |
| 111.     | 3020  | ExchangeQueueItemRepeatedFromOrchestrator        | Очередь обмена для роботов - повторение элемента из оркестратора |
| 112.     | 3021  | ExchangeQueueEditValueByKey                      | Очередь обмена для роботов - изменение значения элемента |
| 113.     | 3022  | ExchangeQueueReadedItemsWithLock                 | Очередь обмена для роботов - чтение элементов по фильтру с блокировкой |
| 114.     | 3023  | ExchangeQueueUnlockItems                         | Очередь обмена для роботов - снятие блокировки с элементов |
| 115.     | 3024  | ExchangeQueueReadedByKeyWithLock                 | Очередь обмена для роботов - чтение элемента по ключу с блокировкой |
| 116.      | 4001  | RobotGroupCreated                                | Группа роботов создана              |
| 117.      | 4002  | RobotGroupChanged                                | Группа роботов изменена             |
| 118.      | 4003  | RobotGroupDeleted                                | Группа роботов удалена              |
| 119.      | 4004  | RobotGroupAddedRobots                            | В группу роботов добавлены роботы   |
| 120.      | 4005  | RobotGroupDeletedRobots                          | Из группы роботов удалены роботы    |
| 121.      | 5000  | ProjectQueuePurged                               | Очередь проектов на выполнение очищена |
| 122.      | 6000  | ScheduleCreated                                  | Расписание создано                  |
| 123.      | 6001  | ScheduleChanged                                  | Расписание изменено                 |
| 124.      | 6002  | ScheduleDeleted                                  | Расписание удалено                  |
| 125.      | 7001  | AgentDeployTrackingStart                         | Развертывание робота - Процесс запущен |
| 126.      | 7010  | AgentDeployTrackingCopyingRobotDistr             | Развертывание робота - Скачивание дистрибутива Робота с Оркестратора |
| 127.      | 7011  | AgentDeployTrackingSaveRobotDistr                | Развертывание робота - Сохранение дистрибутива Робота на машине Робота |
| 128.      | 7020  | AgentDeployTrackingKillRobotProcess              | Развертывание робота - Уничтожение процесса Робота, если такой есть запущенный |
| 129.      | 7030  | AgentDeployTrackingUnpackRobotDistr              | Развертывание робота - Распаковка дистрибутива Робота |
| 130.      | 7040  | AgentDeployTrackingImportingSSLCert              | Развертывание робота - Импорт ssl-сертификата из дистрибутива Робота в хранилище сертификатов ОС |
| 131.      | 7050  | AgentDeployTrackingTransforRobotConfig           | Развертывание робота - Трансформация конфига Робота под параметры деплоя                                    |
| 132.       | 7060  | AgentDeployTrackingReservationUrlWithOrchPort    | Развертывание робота - Резервирование url+port для https-службы Робота с port, переданным Оркестратором     |
| 133.       | 7061  | AgentDeployTrackingReservationUrlWithActualPort  | Развертывание робота - url зарезервирован для port, резервировать с первым свободным после переданного port |
| 134.       | 7070  | AgentDeployTrackingBindingSSLCertToRobotService  | Развертывание робота - Привязка ssl-сертификата к службе робота |
| 135.       | 8001  | AgentStartRobotTrackingStart                     | Старт робота - Процесс запущен  |
| 136.       | 8010  | AgentStartRobotTrackingDownloadProjectArch       | Старт робота - Скачивание архива проекта с Оркестратора |
| 137.       | 8011  | AgentStartRobotTrackingSaveProjectArch           | Старт робота - Сохранение архива проекта на машине Робота |
| 138.       | 8020  | AgentStartRobotTrackingKillRobotProcess          | Старт робота - Уничтожение процесса Робота, если такой есть запущенный |
| 139.       | 8021  | AgentStartRobotTrackingGenerateRunScript         | Старт робота - Генерация скрипта запуска Робота |
| 140.       | 8022  | AgentStartRobotTrackingCreateTaskToStartRobot    | Старт робота - Создание Windows Task запуска Робота (для Windows 2016 Server) |
| 141.       | 8023  | AgentStartRobotTrackingDirectlyStartRobot        | Старт робота - Непосредственный запуска Робота (для Windows 10) |
| 142.       | 8030  | AgentStartRobotTrackingWaitStartRobot            | Старт робота - Ожидание старта приложения Робота |
| 143.       | 8031  | AgentStartRobotTrackingTakeAvailableRobotLicense | Старт робота - Робот получил свободную лицензию  |
| 144.       | 8040  | AgentStartRobotWaitExecuteWorkflow               | Старт робота - Ожидание выполнения проекта Роботом |
| 145.       | 8050  | AgentStartRobotTrackingExecuteWorkflow           | Старт робота - Проект запущен                    |
| 146.       | 9000  | AssignmentCreated                                | Задание создано                                  |
| 147.       | 9001  | AssignmentChanged                                | Задание изменено                                 |
| 148.       | 9002  | AssignmentDeleted                                | Задание удалено                                  |
| 149.       | 9010  | AssignmentProjectQueued                          | Проект задания поставлен в очередь выполнения    |
| 150.       | 9011  | AssignmentProjectQueuedError                     | Ошибка постановки проекта задания в очередь выполнения |
| 151.       | 9012  | AssignmentStarted                                | Задание запущено                                 |
| 152.       | 9013  | AssignmentPaused                                 | Задание остановлено                              |
| 153.       | 9014  | AssignmentResumed                                | Задание возобновлено                             |
| 154.       | 9015  | AssignmentCompleted                              | Задание выполнено                                |
| 155.       | 10000 | RpaProjectQueueProcessingTypeChanged             | Параметры обработки очереди на выполнение проектов изменены  |
| 156.       | 20000 | LogsTruncate                                     | Очистка логов                                    |
| 157.       | 20001 | LogsDumpStarted                                  | Выгрузка логов запущена                          |
| 158.       | 20002 | LogsDumpCompleted                                | Выгрузка логов завершена                         |
| 159.       | 30001 | ProductionCalendarsCreated                       | Создание производственного календаря             |
| 160.       | 30002 | ProductionCalendarsChanged                       | Изменение производственного календаря            |
| 161.       | 30003 | ProductionCalendarsDeleted                       | Удаление производственного календаря             |
| 162.       | 40001 | AgentCreated                                     | Агент создан             |
| 163.       | 40002 | AgentChanged                                     | Агент изменен             |
| 164.       | 40003 | AgentDeleted                                     | Агент удален             |
| 165.       | 40004 | AgentTestAvailable                               | Агент доступен             |
| 166.       | 40005 | AgentTestNotAvailable                            | Агент недоступен             |
| 167.       | 40006 | AgentEnabledKeepRDPSession                       | Агент - EnabledKeepRDPSession |
| 168.       | 40007 | AgentDisabledKeepRDPSession                      | Агент - DisabledKeepRDPSession  |
| 169.       | 40008 | AgentEnabledKeepRDPSessionError                  | Агент - EnabledKeepRDPSessionError |
| 170.       | 50001 | TenantCreated                                    | Тенант создан             |
| 171.       | 50002 | TenantChanged                                    | Тенант изменен          |
| 172.       | 50003 | TenantDisabled                                   | Тенант выведен из эксплуатации |
| 173.       | 60001 | TriggerScheduleFired                             | Сработал триггер расписания    |
| 174.       | 60002 | TriggerEmailFired                                | Сработал триггер Email             |
| 175.       | 60003 | TriggerExchangeQueueFired                      | Сработал триггер очереди обмена данными |
| 176.       | 60004 | TriggerFolderFired                               | Сработал триггер папки             |
| 177.       | 60005 | TriggerProjectCompletedFired                     | Сработал триггер завершения проекта |
| 178.       | 60006 | TriggerFromRobotFired                        | Сработал триггер запуска задания из робота|
| 179.       | 70001 | IncomingEmailCreated                             | Создание Email для входящей почты  |
| 180.       | 70002 | IncomingEmailChanged                             | Изменение Email для входящей почты |
| 181.       | 70003 | IncomingEmailDeleted                             | Удаление Email для входящей почты  |
| 182.       | 80001 | FolderCreated                                    | Создание личной папки             |
| 183.       | 80002 | FolderChanged                                    | Изменение личной папки            |
| 184.       | 80003 | FolderDeleted                                    | Удаление личной папки             |
| 185.       | 80004 | FolderResubordination                            | Переподчинение личной папки       |
| 186.       | 80005 | FolderMoveObjects                                | Перемещение объектов в личную папку |
| 187.       | 80006 | FolderMissingProject                             | Проект отсутствует в личной папке  |
| 188.       | 80007 | FolderMissingRobots                              | В личной папке отсутствуют роботы  |
| 189.       | 90001 | GrantUserWorker                              | Предоставление пользователю машина робота |
| 190.       | 90002 | GrantUserWorkerCanceled             | Предоставление пользователю машина робота отменено |
| 191.       | 90003 | GrantUserAgent                                   | Предоставление пользователю агента |
| 192.       | 90004 | GrantUserAgentCanceled                     | Предоставление пользователю агента отменено |
| 193.       | 90101 | UserGrantCreated                                 | Наследование объектов создано       |
| 194.       | 90102 | UserGrantChanged                                 | Наследование объектов изменено      |
| 195.       | 90103 | UserGrantDeleted                                 | Наследование объектов удалено  |
| 196.       |       | ProjectRobotServiceBreakAssignmentNotAllowOverlay | Проект запущен по заданию и еще не завершен (RobotService) |
| 197.       |       | ProjectRobotServiceBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (RobotService) |
| 198.       |       | ProjectRobotStartBreakAssignmentNotAllowOverlay | Проект запущен по заданию и еще не завершен (RobotStart) |
| 199.       |       | ProjectRobotStartBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (RobotStart) |
| 200.       |       | ProjectQueueBreakProjectLimitedLaunch      | Проект запущен в максимальном количестве экземпляров (Queue)      |

Список событий может быть изменен в следующих версиях Оркестратора.
