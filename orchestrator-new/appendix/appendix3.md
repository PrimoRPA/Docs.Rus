# Приложение 3 - События Оркестратора

:small_blue_diamond: В зависимости от используемой версии Оркестратора список событий может различаться.

Таблица 1 – Перечень событий Оркестратора

| №п/п | Код | Наименование | Описание |
| --- | --- | --- | --- |
| 1. | 1 | OrchestratorStarted | Оркестратор стартовал |
| 2. | 101 | UserCreated | Пользователь создан |
| 3. | 102 | AdUserCreated | Пользователь AD зарегистрирован |
| 4. | 103 | UserChanged | Пользователь изменен |
| 5. | 104 | UserDisabled | Пользователь отключен |
| 6. | 106 | UserEnabled | Пользователь включен |
| 7. | 107 | UserDeleted | Пользователь удален |
| 8. | 105 | UserRolesAssigned | Пользователю назначены роли |
| 9. | 108 | UserPasswordChanged | Пользователь изменил свой пароль |
| 10. | 201 | RoleCreated | Роль создана |
| 11. | 202 | RoleChanged | Роль изменена |
| 12. | 203 | RoleDeleted | Роль удалена |
| 13. | 204 | RolePermissionsAssigned | Роли назначены права |
| 14. | 301 | WorkerCreated | Машина зарегистрирована |
| 15. | 302 | WorkerChanged | Машина изменена |
| 16. | 303 | WorkerDisabled | Машина выведена из эксплуатации |
| 17. | 304 | WorkerRebootStarted | Перезагрузка машины запущена |
| 18. | 305 | WorkerRebootCompleted | Перезагрузка машины завершена |
| 19. | 306 | WorkerTestAvailable | Машина доступна |
| 20. | 307 | WorkerTestNotAvailable | Машина недоступна |
| 21. | 308 | WorkerIpAddressSended | Машина робота отправила свой IP Оркестратору |
| 22. | 401 | ProjectCreated | Проект создан |
| 23. | 402 | ProjectChanged | Проект изменен |
| 24. | 403 | ProjectDisabled | Проект выведен из эксплуатации |
| 25. | 404 | ProjectRun | Проект запущен |
| 26. | 405 | ProjectAddedRobot | К проекту добавлен робот |
| 27. | 406 | ProjectDeletedRobot | Из проекта удален робот |
| 28. | 407 | ProjectChangedRobotOrder | Изменение приоритета роботов проекта |
| 29. | 408 | ProjectEnqueue | Проект добавлен в очередь выполнения |
| 30. | 410 | ProjectReEnqueue | Проект добавлен в очередь выполнения повторно |
| 31. | 409 | ProjectPeek | Проект извлечен из очереди выполнения |
| 32. | 411 | ProjectSwappedMainVersionUp | Проект назначен главной версией |
| 33. | 412 | ProjectSwappedMainVersionDown | Проект больше не является главной версией |
| 34. | 413 | ProjectVersionCreated | Версия проекта создана |
| 35. | 414 | ProjectDeletedFromQueue | Проект удален из очереди на выполнение |
| 36. | 415 | ProjectDownloaded | Скачан архив проекта |
| 37. | 501 | RobotCreated | Робот зарегистрирован |
| 38. | 502 | RobotDisabled | Робот выведен из эксплуатации |
| 39. | 503 | RobotDeployStarted | Развертывание робота запущено |
| 40. | 504 | RobotStartStarted | Старт робота запущен |
| 41. | 505 | RobotStartCompleted | Старт робота завершен |
| 42. | 506 | RobotEraseStarted | Стирание робота запущено |
| 43. | 507 | RobotEraseCompleted | Стирание робота завершено |
| 44. | 508 | RobotProjectRun | Проект на роботе запущен |
| 45. | 509 | RobotProjectStopped | Проект на роботе остановлен |
| 46. | 510 | RobotDeployCompleted | Развертывание робота завершено |
| 47. | 511 | RobotStartError | Ошибка при запуске робота |
| 48. | 512 | RobotProjectCompletedSuccess | Зафиксировано удачное завершение выполнения проекта роботом |
| 49. | 513 | RobotProjectCompletedError | Зафиксировано неудачное завершение выполнения проекта роботом |
| 50. | 514 | RobotHardKillStarted | Старт принудительной остановки робота |
| 51. | 515 | RobotHardKillCompleted | Принудительная остановка робота завершена |
| 52. | 516 | RobotSoftKillStarted | Старт мягкой остановки робота |
| 53. | 517 | RobotSoftKillCompleted | Мягкая остановка робота завершена |
| 54. | 518 | RobotStartedFromAssignment | Робот запущен из задания |
| 55. | 601 | LicenseAdded | Лицензия добавлена |
| 56. | 602 | LicenseDeleted | Лицензия удалена |
| 57. | 603 | LicenseDownloaded | Лицензия скачана |
| 58. | 604 | LicenseRevoked | Лицензия отозвана |
| 59. | 605 | LicenseRevokeReplaced | Отозванная лицензия заменена |
| 60. | 606 | LicenseRequested | Создан запрос на новую лицензию |
| 61. | 607 | LicenseReplaceRequested | Создан запрос на замен лицензии |
| 62. | 608 | LicenseTakeAvailableRobotOk | Робот занял свободную лицензию |
| 63. | 609 | LicenseTakeAvailableRobotError | Ошибка занятия лицензии роботом |
| 64. | 610 | LicenseRobotReleaseOk | Лицензия робота освобождена |
| 65. | 611 | LicenseRobotReleaseError | Ошибка освобождения лицензии робота |
| 66. | 612 | LicenseToTenantAdded | Лицензия выдана на тенант |
| 67. | 613 | LicenseTakeAvailableStudioOk | Студия заняла свободную лицензию |
| 68. | 614 | LicenseTakeAvailableStudioError | Ошибка занятия лицензии студией |
| 69. | 615 | LicenseStudioTimeoutRelease | Лицензия студии освобождена по таймауту |
| 70. | 616 | LicenseRobotTimeoutRelease | Лицензия робота освобождена по таймауту |
| 71. | 617 | LicenseTakeAvailableAttendedRobotOk | Аттендед робот занял свободную лицензию |
| 72. | 618 | LicenseTakeAvailableAttendedRobotError | Ошибка занятия лицензии аттендед роботом |
| 73. | 619 | LicenseAttendedRobotReleaseOk | Лицензия аттендед робота освобождена |
| 74. | 620 | LicenseAttendedRobotReleaseError | Ошибка освобождения лицензии аттендед робота |
| 75. | 701 | AssetCreated | Ресурс создан |
| 76. | 702 | AssetChanged | Ресурс изменен |
| 77. | 703 | AssetDeleted | Ресурс удален |
| 78. | 801 | DeployTemplateCreated | Шаблон развертывания создан |
| 79. | 802 | DeployTemplateChanged | Шаблон развертывания изменен |
| 80. | 803 | DeployTemplateDisabled | Шаблон развертывания выведен из эксплуатации |
| 81. | 1201 | RobotDistrUploaded | Дистрибутив робота загружен |
| 82. | 1202 | RobotDistrActivated | Дистрибутив робота активирован |
| 83. | 1203 | RobotDistrDeleted | Дистрибутив робота удален |
| 84. | 2001 | Login | Пользователь авторизовался |
| 85. | 2002 | LoginUserNotExist | Пользователь не существует |
| 86. | 2003 | LoginUserLocked | Пользователь заблокирован |
| 87. | 2004 | LoginUserUnauthorized | Ошибка авторизации |
| 88. | 2005 | LoginUserUnauthorizedAD | Ошибка авторизации в AD |
| 89. | 2006 | LoginUserNoRightsGroupAD | Группа AD не имеет привязки к роли |
| 90. | 2007 | LogOut | Пользователь вышел из системы |
| 91. | 3001 | ExchangeQueueCreated | Очередь обмена для роботов создана |
| 92. | 3002 | ExchangeQueueChanged | Очередь обмена для роботов изменена |
| 93. | 3003 | ExchangeQueueDeleted | Очередь обмена для роботов удалена |
| 94. | 3004 | ExchangeQueuePermissionsAssigned | Очередь обмена для роботов - назначены права |
| 95. | 3005 | ExchangeQueueEnqueue | Очередь обмена для роботов - добавление значения |
| 96. | 3006 | ExchangeQueuePeek | Очередь обмена для роботов - извлечение значения |
| 97. | 3007 | ExchangeQueueReadedByKey | Очередь обмена для роботов - извлечение значения по ключу |
| 98. | 3008 | ExchangeQueueRemovedByKey | Очередь обмена для роботов - удаление значения по ключу |
| 99. | 3009 | ExchangeQueueChangeStatusByKey | Очередь обмена для роботов - изменение статуса элемента по ключу |
| 100. | 4001 | RobotGroupCreated | Группа роботов создана |
| 101. | 4002 | RobotGroupChanged | Группа роботов изменена |
| 102. | 4003 | RobotGroupDeleted | Группа роботов удалена |
| 103. | 4004 | RobotGroupAddedRobots | В группу роботов добавлены роботы |
| 104. | 4005 | RobotGroupDeletedRobots | Из группы роботов удалены роботы |
| 105. | 5000 | ProjectQueuePurged | Очередь проектов на выполнение очищена |
| 106. | 6000 | ScheduleCreated | Расписание создано |
| 107. | 6001 | ScheduleChanged | Расписание изменено |
| 108. | 6002 | ScheduleDeleted | Расписание удалено |
| 109. | 7001 | AgentDeployTrackingStart | Разворачивание робота - Процесс запущен |
| 110. | 7010 | AgentDeployTrackingCopyingRobotDistr | Разворачивание робота - Скачивание дистрибутива Робота с Оркестратора |
| 111. | 7011 | AgentDeployTrackingSaveRobotDistr | Разворачивание робота - Сохранение дистрибутива Робота на машине Робота |
| 112. | 7020 | AgentDeployTrackingKillRobotProcess | Разворачивание робота - Уничтожение процесса Робота, если такой есть запущенный |
| 113. | 7030 | AgentDeployTrackingUnpackRobotDistr | Разворачивание робота - Распаковка дистрибутива Робота |
| 114. | 7040 | AgentDeployTrackingImportingSSLCert | Разворачивание робота - Импорт ssl-сертификата из дистрибутива Робота в хранилище сертификатов ОС |
| 115. | 7050 | AgentDeployTrackingTransforRobotConfig | Разворачивание робота - Трансформация конфига Робота под параметры деплоя |
| 116. | 7060 | AgentDeployTrackingReservationUrlWithOrchPort | Разворачивание робота - Резервирование url+port для https-службы Робота с port, переданным Оркестратором |
| 117. | 7061 | AgentDeployTrackingReservationUrlWithActualPort | Разворачивание робота - url зарезервирован для port, резервировать с первым свободным после переданного port |
| 118. | 7070 | AgentDeployTrackingBindingSSLCertToRobotService | Разворачивание робота - Привязка ssl-сертификата к службе робота |
| 119. | 8001 | AgentStartRobotTrackingStart | Старт робота - Процесс запущен |
| 120. | 8010 | AgentStartRobotTrackingDownloadProjectArch | Старт робота - Скачивание архива проекта с Оркестратора |
| 121. | 8011 | AgentStartRobotTrackingSaveProjectArch | Старт робота - Сохранение архива проекта на машине Робота |
| 122. | 8020 | AgentStartRobotTrackingKillRobotProcess | Старт робота - Уничтожение процесса Робота, если такой есть запущенный |
| 123. | 8021 | AgentStartRobotTrackingGenerateRunScript | Старт робота - Генерация скрипта запуска Робота |
| 124. | 8022 | AgentStartRobotTrackingCreateTaskToStartRobot | Старт робота - Создание Windows Task запуска Робота (для Windows 2016 Server) |
| 125. | 8023 | AgentStartRobotTrackingDirectlyStartRobot | Старт робота - Непосредственный запуска Робота (для Windows 10) |
| 126. | 8030 | AgentStartRobotTrackingWaitStartRobot | Старт робота - Ожидание старта приложения Робота |
| 127. | 8031 | AgentStartRobotTrackingTakeAvailableRobotLicense | Старт робота - Робот получил свободную лицензию |
| 128. | 8040 | AgentStartRobotWaitExecuteWorkflow | Старт робота - Ожидание выполнения проекта Роботом |
| 129. | 8050 | AgentStartRobotTrackingExecuteWorkflow | Старт робота - Проект запущен |
| 130. | 9000 | AssignmentCreated | Задание создано |
| 131. | 9001 | AssignmentChanged | Задание изменено |
| 132. | 9002 | AssignmentDeleted | Задание удалено |
| 133. | 9010 | AssignmentProjectQueued | Проект задания поставлен в очередь выполнения |
| 134. | 9011 | AssignmentProjectQueuedError | Ошибка постановки проекта задания в очередь выполнения |
| 135. | 9012 | AssignmentStarted | Задание запущено |
| 136. | 9013 | AssignmentPaused | Задание остановлено |
| 137. | 9014 | AssignmentResumed | Задание возобновлено |
| 138. | 9015 | AssignmentCompleted | Задание выполнено |
| 139. | 10000 | RpaProjectQueueProcessingTypeChanged | Параметры обработки очереди на выполнение проектов изменены |
| 140. | 20000 | LogsTruncate | Очистка логов |
| 141. | 20001 | LogsDumpStarted | Выгрузка логов запущена |
| 142. | 20002 | LogsDumpCompleted | Выгрузка логов завершена |
| 143. | 30001 | ProductionCalendarsCreated | Создание производственного календаря |
| 144. | 30002 | ProductionCalendarsChanged | Изменение производственного календаря |
| 145. | 30003 | ProductionCalendarsDeleted | Удаление производственного календаря |
| 146. | 40001 | AgentCreated | Агент создан |
| 147. | 40002 | AgentChanged | Агент изменен |
| 148. | 40003 | AgentDeleted | Агент удален |
| 149. | 40004 | AgentTestAvailable | Агент доступен |
| 150. | 40005 | AgentTestNotAvailable | Агент недоступен |
| 151. | 40006 | AgentEnabledKeepRDPSession | Агент - EnabledKeepRDPSession |
| 152. | 40007 | AgentDisabledKeepRDPSession | Агент - DisabledKeepRDPSession |
| 153. | 40008 | AgentEnabledKeepRDPSessionError | Агент - EnabledKeepRDPSessionError |
| 154. | 50001 | TenantCreated | Тенант создан |
| 155. | 50002 | TenantChanged | Тенант изменен |
| 156. | 50003 | TenantDisabled | Тенант выведен из эксплуатации |
| 157. | 60001 | TriggerScheduleFired | Сработал триггер расписания |
| 158. | 60002 | TriggerEmailFired | Сработал триггер Email |
| 159. | 60003 | TriggerExchangeQueueFired | Сработал триггер очереди обмена данными |
| 160. | 60004 | TriggerFolderFired | Сработал триггер папки |
| 161. | 60005 | TriggerProjectCompletedFired | Сработал триггер завершения проекта |
| 162. | 70001 | IncomingEmailCreated | Создание Email для входящей почты |
| 163. | 70002 | IncomingEmailChanged | Изменение Email для входящей почты |
| 164. | 70003 | IncomingEmailDeleted | Удаление Email для входящей почты |
| 165. | 80001 | FolderCreated | Создание личной папки |
| 166. | 80002 | FolderChanged | Изменение личной папки |
| 167. | 80003 | FolderDeleted | Удаление личной папки |
| 168. | 80004 | FolderResubordination | Переподчинение личной папки |
| 169. | 80005 | FolderMoveObjects | Перемещение объектов в личную папку |
| 170. | 80006 | FolderMissingProject | Проект отсутствует в личной папке |
| 171. | 80007 | FolderMissingRobots | В личной папке отсутствуют роботы |

Список событий может быть изменен в следующих версиях Оркестратора.
