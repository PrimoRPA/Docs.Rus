# Приложение 3 - События Оркестратора

Таблица 1. – *Перечень событий Оркестратора*:

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
| 41.                    | 504   | RobotStartStarted                                | Старт робота запущен                                                                                        |
| 42.                    | 505   | RobotStartCompleted                              | Старт робота завершен                                                                                       |
| 43.                    | 506   | RobotEraseStarted                                | Стирание робота запущено                                                                                    |
| 44.                    | 507   | RobotEraseCompleted                              | Стирание робота завершено                                                                                   |
| 45.                    | 508   | RobotProjectRun                                  | Проект на роботе запущен                                                                                    |
| 46.                    | 509   | RobotProjectStopped                              | Проект на роботе остановлен                                                                                 |
| 47.                    | 510   | RobotDeployCompleted                             | Развертывание робота завершено                                                                              |
| 48.                    | 511   | RobotStartError                                  | Ошибка при запуске робота                                                                                   |
| 49.                    | 512   | RobotProjectCompletedSuccess                     | Зафиксировано удачное завершение выполнения проекта роботом                                                 |
| 50.                    | 513   | RobotProjectCompletedError                       | Зафиксировано не удачное завершение выполнения проекта роботом                                              |
| 49.                    | 514   | RobotHardKillStarted                             | Старт принудительной остановки робота                                                                       |
| 50.                    | 515   | RobotHardKillCompleted                           | Принудительная остановка робота завершена                                                                   |
| 51.                    | 516   | RobotSoftKillStarted                             | Старт мягкой остановки робота                                                                               |
| 52.                    | 517   | RobotSoftKillCompleted                           | Мягкая остановка робота завершена                                                                           |
| 53.                    | 601   | LicenseAdded                                     | Лицензия добавлена                                                                                          |
| 54.                    | 602   | LicenseDeleted                                   | Лицензия удалена                                                                                            |
| 55.                    | 603   | LicenseDownloaded                                | Лицензия скачана                                                                                            |
| 56.                    | 604   | LicenseRevoked                                   | Лицензия отозвана                                                                                           |
| 57.                    | 605   | LicenseRevokeReplaced                            | Отозванная лицензия заменена                                                                                |
| 58.                    | 606   | LicenseRequested                                 | Создан запрос на новую лицензию                                                                             |
| 59.                    | 607   | LicenseReplaceRequested                          | Создан запрос на замен лицензии                                                                             |
| 60.                    | 608   | LicenseTakeAvailableRobotOk                      | Робот занял свободную лицензию                                                                              |
| 61.                    | 609   | LicenseTakeAvailableRobotError                   | Ошибка занятия лицензии роботом                                                                             |
| 62.                    | 610   | LicenseRobotReleaseOk                            | Лицензия робота освобождена                                                                                 |
| 63.                    | 611   | LicenseRobotReleaseError                         | Ошибка освобождения лицензии робота                                                                         |
| 64.                    | 612   | LicenseToTenantAdded                             | Лицензия выдана на тенант                                                                                   |
| 65.                    | 613   | LicenseTakeAvailableStudioOk                     | Студия заняла свободную лицензию                                                                            |
| 66.                    | 614   | LicenseTakeAvailableStudioError                  | Ошибка занятия лицензии студией                                                                             |
| 67.                    | 615   | LicenseStudioTimeoutRelease                      | Лицензия студии освобождена по таймауту                                                                     |
| 68.                    | 616   | LicenseRobotTimeoutRelease                       | Лицензия робота освобождена по таймауту                                                                     |
| 69.                    | 701   | AssetCreated                                     | Ресурс создан                                                                                               |
| 70.                    | 702   | AssetChanged                                     | Ресурс изменен                                                                                              |
| 71.                    | 703   | AssetDeleted                                     | Ресурс удален                                                                                               |
| 72.                    | 801   | DeployTemplateCreated                            | Шаблон развертывания создан                                                                                 |
| 73.                    | 802   | DeployTemplateChanged                            | Шаблон развертывания изменен                                                                                |
| 74.                    | 803   | DeployTemplateDisabled                           | Шаблон развертывания выведен из эксплуатации                                                                |
| 75.                    | 1101  | ScheduledTaskCreated                             | Задача создана                                                                                              |
| 76.                    | 1102  | ScheduledTaskChanged                             | Задача изменена                                                                                             |
| 77.                    | 1103  | ScheduledTaskDeleted                             | Задача удалена                                                                                              |
| 78.                    | 1104  | ScheduledTaskStarted                             | Задача стартовала                                                                                           |
| 79.                    | 1105  | ScheduledTaskPaused                              | Задача поставлена на паузу                                                                                  |
| 80.                    | 1106  | ScheduledTaskResumed                             | Задача снята с паузы                                                                                        |
| 81.                    | 1107  | ScheduledTaskDisabled                            | Задача выключена                                                                                            |
| 82.                    | 1108  | ScheduledTaskEnabled                             | Задача включена                                                                                             |
| 83.                    | 1201  | RobotDistrUploaded                               | Дистрибутив робота загружен                                                                                 |
| 84.                    | 1202  | RobotDistrActivated                              | Дистрибутив робота активирован                                                                              |
| 85.                    | 1203  | RobotDistrDeleted                                | Дистрибутив робота удален                                                                                   |
| 86.                    | 2001  | Login                                            | Пользователь авторизовался                                                                                  |
| 87.                    | 2002  | LoginUserNotExists                               | Пользователь не существует                                                                                  |
| 88.                    | 2003  | LoginUserLocked                                  | Пользователь заблокирован                                                                                   |
| 89.                    | 2004  | LoginUserUnauthorized                            | Ошибка авторизации                                                                                          |
| 90.                    | 2005  | LoginUserUnauthorizedAD                          | Ошибка авторизации в AD                                                                                     |
| 91.                    | 2006  | LoginUserNoRightsGroupAD                         | Группа AD не имеет привязки к роли                                                                          |
| 92.                    | 2007  | LogOut                                           | Пользователь вышел из системы    |
| 9.                     | 2008   | LoginUserExpired                                | Срок действия учетной записи истек  |

| 93.                    | 3001  | ExchangeQueueCreated                             | Очередь обмена для роботов создана                                                                          |
| 94.                    | 3002  | ExchangeQueueChanged                             | Очередь обмена для роботов изменена                                                                         |
| 95.                    | 3003  | ExchangeQueueDeleted                             | Очередь обмена для роботов удалена                                                                          |
| 96.                    | 3004  | ExchangeQueuePermissionsAssigned                 | Очередь обмена для роботов - назначены права                                                                |
| 97.                    | 3005  | ExchangeQueueEnqueue                             | Очередь обмена для роботов - добавление значения                                                            |
| 98.                    | 3006  | ExchangeQueuePeek                                | Очередь обмена для роботов - извлечение значения                                                            |
| 99.                    | 4001  | RobotGroupCreated                                | Группа роботов создана                                                                                      |
| 100.                   | 4002  | RobotGroupChanged                                | Группа роботов изменена                                                                                     |
| 101.                   | 4003  | RobotGroupDeleted                                | Группа роботов удалена                                                                                      |
| 102.                   | 4004  | RobotGroupAddedRobots                            | В группу роботов добавлены роботы                                                                           |
| 103.                   | 4005  | RobotGroupDeletedRobots                          | Из группы роботов удалены роботы                                                                            |
| 104.                   | 5000  | ProjectQueuePurged                               | Очередь проектов на выполнение очищена                                                                      |
| 105.                   | 6000  | ScheduleCreated                                  | Расписание создано                                                                                          |
| 106.                   | 6001  | ScheduleChanged                                  | Расписание изменено                                                                                         |
| 107.                   | 6002  | ScheduleDeleted                                  | Расписание удалено                                                                                          |
| 108.                   | 7001  | AgentDeployTrackingStart                         | Развертывание робота - Процесс запущен                                                                      |
| 109.                   | 7010  | AgentDeployTrackingCopyingRobotDistr             | Развертывание робота - Скачивание дистрибутива Робота с Оркестратора                                        |
| 110.                   | 7011  | AgentDeployTrackingSaveRobotDistr                | Развертывание робота - Сохранение дистрибутива Робота на машине Робота                                      |
| 111.                   | 7020  | AgentDeployTrackingKillRobotProcess              | Развертывание робота - Уничтожение процесса Робота, если такой есть запущенный                              |
| 112.                   | 7030  | AgentDeployTrackingUnpackRobotDistr              | Развертывание робота - Распаковка дистрибутива Робота                                                       |
| 113.                   | 7040  | AgentDeployTrackingImportingSSLCert              | Развертывание робота - Импорт ssl-сертификата из дистрибутива Робота в хранилище сертификатов ОС            |
| 114.                   | 7050  | AgentDeployTrackingTransforRobotConfig           | Развертывание робота - Трансформация конфига Робота под параметры деплоя                                    |
| 115.                   | 7060  | AgentDeployTrackingReservationUrlWithOrchPort    | Развертывание робота - Резервирование url+port для https-службы Робота с port, переданным Оркестратором     |
| 116.                   | 7061  | AgentDeployTrackingReservationUrlWithActualPort  | Развертывание робота - url зарезервирован для port, резервировать с первым свободным после переданного port |
| 117.                   | 7070  | AgentDeployTrackingBindingSSLCertToRobotService  | Развертывание робота - Привязка ssl-сертификата к службе робота                                             |
| 118.                   | 8001  | AgentStartRobotTrackingStart                     | Старт робота - Процесс запущен                                                                              |
| 119.                   | 8010  | AgentStartRobotTrackingDownloadProjectArch       | Старт робота - Скачивание архива проекта с Оркестратора                                                     |
| 120.                   | 8011  | AgentStartRobotTrackingSaveProjectArch           | Старт робота - Сохранение архива проекта на машине Робота                                                   |
| 121.                   | 8020  | AgentStartRobotTrackingKillRobotProcess          | Старт робота - Уничтожение процесса Робота, если такой есть запущенный                                      |
| 122.                   | 8021  | AgentStartRobotTrackingGenerateRunScript         | Старт робота - Генерация скрипта запуска Робота                                                             |
| 123.                   | 8022  | AgentStartRobotTrackingCreateTaskToStartRobot    | Старт робота - Создание Windows Task запуска Робота (для Windows 2016 Server)                               |
| 124.                   | 8023  | AgentStartRobotTrackingDirectlyStartRobot        | Старт робота - Непосредственный запуска Робота (для Windows 10)                                             |
| 125.                   | 8030  | AgentStartRobotTrackingWaitStartRobot            | Старт робота - Ожидание старта приложения Робота                                                            |
| 126.                   | 8031  | AgentStartRobotTrackingTakeAvailableRobotLicense | Старт робота - Робот получил свободную лицензию                                                             |
| 127.                   | 8040  | AgentStartRobotWaitExecuteWorkflow               | Старт робота - Ожидание выполнения проекта Роботом                                                          |
| 128.                   | 8050  | AgentStartRobotTrackingExecuteWorkflow           | Старт робота - Проект запущен                                                                               |
| 129.                   | 9000  | AssignmentCreated                                | Задание создано                                                                                             |
| 130.                   | 9001  | AssignmentChanged                                | Задание изменено                                                                                            |
| 131.                   | 9002  | AssignmentDeleted                                | Задание удалено                                                                                             |
| 132.                   | 9010  | AssignmentProjectQueued                          | Проект задания поставлен в очередь выполнения                                                               |
| 133.                   | 9011  | AssignmentProjectQueuedError                     | Ошибка постановки проекта задания в очередь выполнения                                                      |
| 134.                   | 9012  | AssignmentStarted                                | Задание запущено                                                                                            |
| 135.                   | 9013  | AssignmentPaused                                 | Задание остановлено                                                                                         |
| 136.                   | 9014  | AssignmentResumed                                | Задание возобновлено                                                                                        |
| 137.                   | 9015  | AssignmentCompleted                              | Задание выполнено                                                                                           |
| 138.                   | 10000 | RpaProjectQueueProcessingTypeChanged             | Параметры обработки очереди на выполнение проектов изменены                                                 |
| 139.                   | 20000 | LogsTruncate                                     | Очистка логов                                                                                               |
| 140.                   | 20001 | LogsDumpStarted                                  | Выгрузка логов запущена                                                                                     |
| 141.                   | 20002 | LogsDumpCompleted                                | Выгрузка логов завершена                                                                                    |
| 142.                   | 30001 | ProductionCalendarsCreated                       | Создание производственного календаря                                                                        |
| 143.                   | 30002 | ProductionCalendarsChanged                       | Изменение производственного календаря                                                                       |
| 144.                   | 30003 | ProductionCalendarsDeleted                       | Удаление производственного календаря                                                                        |

Список событий может быть изменен в следующих версиях Оркестратора.
