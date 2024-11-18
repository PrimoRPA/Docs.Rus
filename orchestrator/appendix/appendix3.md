# Приложение 3 - События Оркестратора

:small_blue_diamond: В зависимости от используемой версии Оркестратора список событий может различаться.

Таблица 1. – Перечень событий Оркестратора.

| №п/п | Код | Наименование | Описание |
| --- | --- | --- | --- |
| 1. | 1 | OrchestratorStarted | Оркестратор стартовал |
| 2. | 2 | ConfigChanged | Конфигурационный файл изменен |
| 3. | 101 | UserCreated | Пользователь создан |
| 4. | 102 | AdUserCreated | Пользователь AD зарегистрирован |
| 5. | 103 | UserChanged | Пользователь изменен |
| 6. | 104 | UserDisabled | Пользователь отключен |
| 7. | 106 | UserEnabled | Пользователь включен |
| 8. | 107 | UserDeleted | Пользователь удален |
| 9. | 105 | UserRolesAssigned | Пользователю назначены роли |
| 10. | 108 | UserPasswordChanged | Пользователь изменил свой пароль |
| 11. | 2008 | LoginUserExpired | Срок действия учетной записи истек |
| 12. | 201 | RoleCreated | Роль создана |
| 13. | 202 | RoleChanged | Роль изменена |
| 14. | 203 | RoleDeleted | Роль удалена |
| 15. | 204 | RolePermissionsAssigned | Роли назначены права |
| 16. | 301 | WorkerCreated | Машина зарегистрирована |
| 17. | 302 | WorkerChanged | Машина изменена |
| 18. | 303 | WorkerDisabled | Машина выведена из эксплуатации |
| 19. | 304 | WorkerRebootStarted | Перезагрузка машины запущена |
| 20. | 305 | WorkerRebootCompleted | Перезагрузка машины завершена |
| 21. | 306 | WorkerTestAvailable | Машина доступна |
| 22. | 307 | WorkerTestNotAvailable | Машина недоступна |
| 23. | 308 | WorkerIpAddressSended | Машина робота отправила свой IP Оркестратору |
| 24. | 309 | WorkerLogOffAll | Разлогинивание всех RDP-пользователей |
| 25. | 310 | WorkerIncreaseLoading | На машине робота растет нагрузка |
| 26. | 311 | WorkerDecreaseLoading | На машине робота падает нагрузка |
| 27. | 312 | WorkerOverflowLoading | На машине робота нагрузка превышает допустимую |
| 28. | 315 | WorkerDeleteTSPortsCompleted | Очистка TS портов на машине завершена |
| 29. | 401 | ProjectCreated | Проект создан |
| 30. | 402 | ProjectChanged | Проект изменен |
| 31. | 403 | ProjectDisabled | Проект выведен из эксплуатации |
| 32. | 404 | ProjectRun | Проект запущен |
| 33. | 405 | ProjectAddedRobot | К проекту добавлен робот |
| 34. | 406 | ProjectDeletedRobot | Из проекта/ов удален робот |
| 35. | 407 | ProjectChangedRobotOrder | Изменение приоритета роботов проекта |
| 36. | 408 | ProjectEnqueue | Проект добавлен в очередь выполнения |
| 37. | 410 | ProjectReEnqueue | Проект добавлен в очередь выполнения повторно |
| 38. | 409 | ProjectPeek | Проект извлечен из очереди выполнения |
| 39. | 411 | ProjectSwappedMainVersionUp | Проект назначен главной версией |
| 40. | 412 | ProjectSwappedMainVersionDown | Проект больше не является главной версией |
| 41. | 413 | ProjectVersionCreated | Версия проекта создана |
| 42. | 414 | ProjectDeletedFromQueue | Проект удален из очереди на выполнение |
| 43. | 415 | ProjectDownloaded | Скачан архив проекта |
| 44. | 417 | ProjectVariablesChanged | Переменные проекта изменены |
| 45. | 418 | ProjectArchiveIdRequested | ProjectArchiveId запрошен агентом |
| 46. | 416 | ProjectArchiveUploaded | Архив проекта загружен |
| 47. | 419 | ProjectTagsAdded | К проекту добавлены теги |
| 48. | 420 | ProjectTagsDeleted | У проекта удалены теги |
| 49. | 421 | ProjectNotEnqueue | Проект не добавлен в очередь выполнения |
| 50. | 422 | ProjectRobotServiceBreakAssignmentNotAllowOverlay | Проект запущен по заданию и еще не завершен (RobotService) |
| 51. | 423 | ProjectRobotServiceBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (RobotService) |
| 52. | 424 | ProjectRobotStartBreakAssignmentNotAllowOverlay | Проект запущен по заданию и еще не завершен (RobotStart) |
| 53. | 425 | ProjectRobotStartBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (RobotStart) |
| 54. | 426 | ProjectQueueBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (Queue) |
| 55. | 501 | RobotCreated | Робот зарегистрирован |
| 56. | 502 | RobotDisabled | Робот выведен из эксплуатации |
| 57. | 503 | RobotDeployStarted | Развертывание робота запущено |
| 58. | 504 | RobotStartStarted | Старт робота запущен |
| 59. | 505 | RobotStartCompleted | Старт робота завершен |
| 60. | 506 | RobotEraseStarted | Стирание робота запущено |
| 61. | 507 | RobotEraseCompleted | Стирание робота завершено |
| 62. | 508 | RobotProjectRun | Проект на роботе запущен |
| 63. | 509 | RobotProjectStopped | Проект на роботе остановлен |
| 64. | 510 | RobotDeployCompleted | Развертывание робота завершено |
| 65. | 511 | RobotStartError | Ошибка при запуске робота |
| 66. | 512 | RobotProjectCompletedSuccess | Зафиксировано удачное завершение выполнения проекта роботом |
| 67. | 513 | RobotProjectCompletedError | Зафиксировано не удачное завершение выполнения проекта роботом |
| 68. | 514 | RobotHardKillStarted | Старт принудительной остановки робота |
| 69. | 515 | RobotHardKillCompleted | Принудительная остановка робота завершена |
| 70. | 516 | RobotSoftKillStarted | Старт мягкой остановки робота |
| 71. | 517 | RobotSoftKillCompleted | Мягкая остановка робота завершена |
| 72. | 518 | RobotStartedFromAssignment | Робот запущен из задания |
| 73. | 519 | RobotUnavailableRDPLogOff | Робот недоступен - RDPLogOff |
| 74. | 520 | RobotStartedFromAssignmentError | Ошибка запуска робота из задания |
| 75. | 521 | RobotManualAgentUnlocked | Ручная разблокировка робота, заблокированного агентом |
| 76. | 522 | RobotDeletedProject | У робота удален проект/ы |
| 77. | 523 | RobotManualAgentUnlockedError | Ошибка ручной разблокировки робота, заблокированного агентом |
| 78. | 601 | LicenseAdded | Лицензия добавлена |
| 79. | 602 | LicenseDeleted | Лицензия удалена |
| 80. | 603 | LicenseDownloaded | Лицензия скачана |
| 81. | 604 | LicenseRevoked | Лицензия отозвана |
| 82. | 605 | LicenseRevokeReplaced | Отозванная лицензия заменена |
| 83. | 606 | LicenseRequested | Создан запрос на новую лицензию |
| 84. | 607 | LicenseReplaceRequested | Создан запрос на замен лицензии |
| 85. | 608 | LicenseTakeAvailableRobotOk | Робот занял свободную лицензию |
| 86. | 609 | LicenseTakeAvailableRobotError | Ошибка занятия лицензии роботом |
| 87. | 610 | LicenseRobotReleaseOk | Лицензия робота освобождена |
| 88. | 611 | LicenseRobotReleaseError | Ошибка освобождения лицензии робота |
| 89. | 612 | LicenseToTenantAdded | Лицензия выдана на тенант |
| 90. | 613 | LicenseTakeAvailableStudioOk | Студия заняла свободную лицензию |
| 91. | 614 | LicenseTakeAvailableStudioError | Ошибка занятия лицензии студией |
| 92. | 615 | LicenseStudioTimeoutRelease | Лицензия студии освобождена по таймауту |
| 93. | 616 | LicenseRobotTimeoutRelease | Лицензия робота освобождена по таймауту |
| 94. | 617 | LicenseTakeAvailableAttendedRobotOk | Аттендед робот занял свободную лицензию |
| 95. | 618 | LicenseTakeAvailableAttendedRobotError | Ошибка занятия лицензии аттендед роботом |
| 96. | 619 | LicenseAttendedRobotReleaseOk | Лицензия аттендед робота освобождена |
| 97. | 620 | LicenseAttendedRobotReleaseError | Ошибка освобождения лицензии аттендед робота |
| 98. | 621 | LicenseDeactivated | Лицензия деактивирована |
| 99. | 622 | LicenseActivated | Лицензия активирована после деактивации |
| 100. | 701 | AssetCreated | Ресурс создан |
| 101. | 702 | AssetChanged | Ресурс изменен |
| 102. | 703 | AssetDeleted | Ресурс удален |
| 103. | 801 | DeployTemplateCreated | Шаблон развертывания создан |
| 104. | 802 | DeployTemplateChanged | Шаблон развертывания изменен |
| 105. | 803 | DeployTemplateDisabled | Шаблон развертывания выведен из эксплуатации |
| 106. | 1201 | RobotDistrUploaded | Дистрибутив робота загружен |
| 107. | 1202 | RobotDistrActivated | Дистрибутив робота активирован |
| 108. | 1203 | RobotDistrDeleted | Дистрибутив робота удален |
| 109. | 1204 | NodesDesynchronization | Рассинхронизация дистрибутива робота на узлах |
| 110. | 1205 | NodeSequentialSwitching | Мерцание согласования дистрибутива робота на узле |
| 111. | 2001 | Login | Пользователь авторизовался |
| 112. | 2002 | LoginUserNotExist | Пользователь не существует |
| 113. | 2003 | LoginUserLocked | Пользователь заблокирован |
| 114. | 2004 | LoginUserUnauthorized | Ошибка авторизации |
| 115. | 2005 | LoginUserUnauthorizedAD | Ошибка авторизации в AD |
| 116. | 2006 | LoginUserNoRightsGroupAD | Группа AD не имеет привязки к роли |
| 117. | 2007 | LogOut | Пользователь вышел из системы |
| 118. | 3001 | ExchangeQueueCreated | Очередь обмена для роботов создана |
| 119. | 3002 | ExchangeQueueChanged | Очередь обмена для роботов изменена |
| 120. | 3003 | ExchangeQueueDeleted | Очередь обмена для роботов удалена |
| 121. | 3004 | ExchangeQueuePermissionsAssigned | Очередь обмена для роботов - назначены права |
| 122. | 3005 | ExchangeQueueEnqueue | Очередь обмена для роботов - добавление значения |
| 123. | 3006 | ExchangeQueuePeek | Очередь обмена для роботов - извлечение значения |
| 124. | 3007 | ExchangeQueueReadedByKey | Очередь обмена для роботов - чтение значения по ключу |
| 125. | 3008 | ExchangeQueueRemovedByKey | Очередь обмена для роботов - удаление значения по ключу |
| 126. | 3009 | ExchangeQueueChangeStatusByKey | Очередь обмена для роботов - изменение статуса элемента по ключу |
| 127. | 3010 | ExchangeQueueReEnqueue | Очередь обмена для роботов - повторное помещение элемента в очередь |
| 128. | 3011 | ExchangeQueueAddMetadataByKey | Очередь обмена для роботов - добавление метаданных к элементу по ключу |
| 129. | 3012 | ExchangeQueueReadedItems | Очередь обмена для роботов - чтение элементов по фильтру |
| 130. | 3013 | ExchangeQueueItemTagsAdded | Очередь обмена для роботов - добавление тегов к элементу |
| 131. | 3014 | ExchangeQueueItemTagsDeleted | Очередь обмена для роботов - удаление тегов у элемента |
| 132. | 3015 | ExchangeQueueAddTagsByKey | Очередь обмена для роботов - добавление тегов к элементу по ключу |
| 133. | 3016 | ExchangeQueueEnqueueFromOrchestrator | Очередь обмена для роботов - добавление элемента из оркестратора |
| 134. | 3017 | ExchangeQueueItemChangedFromOrchestrator | Очередь обмена для роботов - изменение элемента из оркестратора |
| 135. | 3018 | ExchangeQueueItemDeletedFromOrchestrator | Очередь обмена для роботов - удаление элемента из оркестратора |
| 136. | 3019 | ExchangeQueueItemClonedFromOrchestrator | Очередь обмена для роботов - клонирование элемента из оркестратора |
| 137. | 3020 | ExchangeQueueItemRepeatedFromOrchestrator | Очередь обмена для роботов - повторение элемента из оркестратора |
| 138. | 3021 | ExchangeQueueEditValueByKey | Очередь обмена для роботов - изменение значения элемента |
| 139. | 3022 | ExchangeQueueReadedItemsWithLock | Очередь обмена для роботов - чтение элементов по фильтру с блокировкой |
| 140. | 3023 | ExchangeQueueUnlockItems | Очередь обмена для роботов - снятие блокировки с элементов |
| 141. | 3024 | ExchangeQueueReadedByKeyWithLock | Очередь обмена для роботов - чтение элемента по ключу с блокировкой |
| 142. | 4001 | RobotGroupCreated | Группа роботов создана |
| 143. | 4002 | RobotGroupChanged | Группа роботов изменена |
| 144. | 4003 | RobotGroupDeleted | Группа роботов удалена |
| 145. | 4004 | RobotGroupAddedRobots | В группу роботов добавлены роботы |
| 146. | 4005 | RobotGroupDeletedRobots | Из группы роботов удалены роботы |
| 147. | 5000 | ProjectQueuePurged | Очередь проектов очищена |
| 148. | 5001 | ProjectQueueItemDeleted | Очередь проектов - удален элемент |
| 149. | 6000 | ScheduleCreated | Расписание создано |
| 150. | 6001 | ScheduleChanged | Расписание изменено |
| 151. | 6002 | ScheduleDeleted | Расписание удалено |
| 152. | 7001 | AgentDeployTrackingStart | Разворачивание робота - Процесс запущен |
| 153. | 7010 | AgentDeployTrackingCopyingRobotDistr | Разворачивание робота - Скачивание дистрибутива Робота с Оркестратора |
| 154. | 7011 | AgentDeployTrackingSaveRobotDistr | Разворачивание робота - Сохранение дистрибутива Робота на машине Робота |
| 155. | 7020 | AgentDeployTrackingKillRobotProcess | Разворачивание робота - Уничтожение процесса Робота, если такой есть запущенный |
| 156. | 7030 | AgentDeployTrackingUnpackRobotDistr | Разворачивание робота - Распаковка дистрибутива Робота |
| 157. | 7040 | AgentDeployTrackingImportingSSLCert | Разворачивание робота - Импорт ssl-сертификата из дистрибутива Робота в хранилище сертификатов ОС |
| 158. | 7050 | AgentDeployTrackingTransforRobotConfig | Разворачивание робота - Трансформация конфига Робота под параметры деплоя |
| 159. | 7060 | AgentDeployTrackingReservationUrlWithOrchPort | Разворачивание робота - Резервирование url+port для https-службы Робота с port, переданным Оркестратором |
| 160. | 7061 | AgentDeployTrackingReservationUrlWithActualPort | Разворачивание робота - url зарезервирован для port, резервировать с первым свободным после переданного port |
| 161. | 7070 | AgentDeployTrackingBindingSSLCertToRobotService | Разворачивание робота - Привязка ssl-сертификата к службе робота |
| 162. | 8001 | AgentStartRobotTrackingStart | Старт робота - Процесс запущен |
| 163. | 8010 | AgentStartRobotTrackingDownloadProjectArch | Старт робота - Скачивание архива проекта с Оркестратора |
| 164. | 8011 | AgentStartRobotTrackingSaveProjectArch | Старт робота - Сохранение архива проекта на машине Робота |
| 165. | 8020 | AgentStartRobotTrackingKillRobotProcess | Старт робота - Уничтожение процесса Робота, если такой есть запущенный |
| 166. | 8021 | AgentStartRobotTrackingGenerateRunScript | Старт робота - Генерация скрипта запуска Робота |
| 167. | 8022 | AgentStartRobotTrackingCreateTaskToStartRobot | Старт робота - Создание Windows Task запуска Робота (для Windows 2016 Server) |
| 168. | 8023 | AgentStartRobotTrackingDirectlyStartRobot | Старт робота - Непосредственный запуск Робота |
| 169. | 8030 | AgentStartRobotTrackingWaitStartRobot | Старт робота - Ожидание старта приложения Робота |
| 170. | 8031 | AgentStartRobotTrackingTakeAvailableRobotLicense | Старт робота - Робот получил свободную лицензию |
| 171. | 8040 | AgentStartRobotWaitExecuteWorkflow | Старт робота - Ожидание выполнения проекта Роботом |
| 172. | 8050 | AgentStartRobotTrackingExecuteWorkflow | Старт робота - Проект запущен |
| 173. | 9000 | AssignmentCreated | Задание создано |
| 174. | 9001 | AssignmentChanged | Задание изменено |
| 175. | 9002 | AssignmentDeleted | Задание удалено |
| 176. | 9010 | AssignmentProjectQueued | Проект задания поставлен в очередь выполнения |
| 177. | 9011 | AssignmentProjectQueuedError | Ошибка постановки проекта задания в очередь выполнения |
| 178. | 9012 | AssignmentStarted | Задание запущено |
| 179. | 9013 | AssignmentPaused | Задание остановлено |
| 180. | 9014 | AssignmentResumed | Задание возобновлено |
| 181. | 9015 | AssignmentCompleted | Задание выполнено |
| 182. | 9016 | AssignmentIncreaseTriggerNativeEventBus | Увеличение очереди событий от триггеров |
| 183. | 9017 | AssignmentDecreaseTriggerNativeEventBus | Уменьшение очереди событий от триггеров |
| 184. | 9018 | AssignmentOverflowTriggerNativeEventBus | Переполнение очереди событий от триггеров |
| 185. | 10000 | RpaProjectQueueProcessingTypeChanged | Параметры обработки очереди на выполнение проектов изменены |
| 186. | 20000 | LogsTruncate | Очистка логов |
| 187. | 20001 | LogsDumpStarted | Выгрузка логов запущена |
| 188. | 20002 | LogsDumpCompleted | Выгрузка логов завершена |
| 189. | 30001 | ProductionCalendarsCreated | Создание производственного календаря |
| 190. | 30002 | ProductionCalendarsChanged | Изменение производственного календаря |
| 191. | 30003 | ProductionCalendarsDeleted | Удаление производственного календаря |
| 192. | 40001 | AgentCreated | Агент создан |
| 193. | 40002 | AgentChanged | Агент изменен |
| 194. | 40003 | AgentDeleted | Агент удален |
| 195. | 40004 | AgentTestAvailable | Агент доступен |
| 196. | 40005 | AgentTestNotAvailable | Агент недоступен |
| 197. | 40006 | AgentEnabledKeepRDPSession | RDP - EnabledKeepRDPSession |
| 198. | 40007 | AgentDisabledKeepRDPSession | RDP - DisabledKeepRDPSession |
| 199. | 40008 | AgentEnabledKeepRDPSessionError | RDP - EnabledKeepRDPSessionError |
| 200. | 40009 | AgentLogOffStarted | RDP - LogOffStarted |
| 201. | 40010 | AgentLogOffCompletedSuccess | RDP - LogOffCompletedSuccess |
| 202. | 40011 | AgentLogOffCompletedError | RDP - LogOffCompletedError |
| 203. | 40012 | AgentMaxAttemptStartLogOff | RDP - MaxAttemptStartLogOff |
| 204. | 40013 | AgentMaxAttemptLogOff | RDP - MaxAttemptLogOff |
| 205. | 40016 | AgentConnectedFlickers | Мерцание RDP-сессии |
| 206. | 50001 | TenantCreated | Тенант создан |
| 207. | 50002 | TenantChanged | Тенант изменен |
| 208. | 50003 | TenantDisabled | Тенант выведен из эксплуатации |
| 209. | 60001 | TriggerScheduleFired | Сработал триггер расписания |
| 210. | 60002 | TriggerEmailFired | Сработал триггер Email |
| 211. | 60003 | TriggerExchangeQueueFired | Сработал триггер очереди обмена данными |
| 212. | 60004 | TriggerFolderFired | Сработал триггер папки |
| 213. | 60005 | TriggerProjectCompletedFired | Сработал триггер завершения проекта |
| 214. | 60006 | TriggerFromRobotFired | Сработал триггер запуска задания из робота |
| 215. | 70001 | IncomingEmailCreated | Создание Email для входящей почты |
| 216. | 70002 | IncomingEmailChanged | Изменение Email для входящей почты |
| 217. | 70003 | IncomingEmailDeleted | Удаление Email для входящей почты |
| 218. | 80001 | FolderCreated | Создание личной папки |
| 219. | 80002 | FolderChanged | Изменение личной папки |
| 220. | 80003 | FolderDeleted | Удаление личной папки |
| 221. | 80004 | FolderResubordination | Переподчинение личной папки |
| 222. | 80005 | FolderMoveObjects | Перемещение объектов в личную папку |
| 223. | 80006 | FolderMissingProject | Проект отсутствует в личной папке |
| 224. | 80007 | FolderMissingRobots | В личной папке отсутствуют роботы |
| 225. | 80021 | Folder2Created | Создание папки |
| 226. | 80022 | Folder2Changed | Изменение папки |
| 227. | 80023 | Folder2Deleted | Удаление папки |
| 228. | 80024 | Folder2Resubordination | Переподчинение папки |
| 229. | 80025 | Folder2MoveObjects | Перемещение объектов в папку |
| 230. | 80026 | Folder2MissingProject | Проект отсутствует в папке |
| 231. | 80027 | Folder2MissingRobots | В папке отсутствуют роботы |
| 232. | 80028 | Folder2GrantOrchUserFolders | Оркестраторному пользователю изменены права на папки |
| 233. | 80029 | Folder2GrantFolderUsers | На папку пользователям изменены права |
| 234. | 90001 | GrantUserWorker | Предоставление пользователю машины робота |
| 235. | 90002 | GrantUserWorkerCanceled | Предоставление пользователю машины робота отменено |
| 236. | 90003 | GrantUserAgent | Предоставление пользователю агента |
| 237. | 90004 | GrantUserAgentCanceled | Предоставление пользователю агента отменено |
| 238. | 90101 | UserGrantCreated | Наследование объектов создано |
| 239. | 90102 | UserGrantChanged | Наследование объектов изменено |
| 240. | 90103 | UserGrantDeleted | Наследование объектов удалено |
| 241. | 90201 | NuGetPackageUploaded | NuGet: пакет закачан в папку оркестратора |
| 242. | 90202 | NuGetPackagePublishStarted | NuGet: публикация пакета запущена |
| 243. | 90203 | NuGetPackagePublishCompletedOk | NuGet: публикация пакета завершена |
| 244. | 90204 | NuGetPackagePublishCompletedError | NuGet: ошибка при публикация пакета |
| 245. | 90205 | NuGetPackageRemoveStarted | NuGet: удаление пакета запущено |
| 246. | 90206 | NuGetPackageRemoveCompletedOk | NuGet: удаление пакета завершено |
| 247. | 90207 | NuGetPackageRemoveCompletedError | NuGet: ошибка при удалении пакета |
| 248. | 90300 | RpaProjectLaunchLogsTransferSuccess | Перенос старых запусков в БД с логами: успешно |
| 249. | 90301 | RpaProjectLaunchLogsTransferError | Перенос старых запусков в БД с логами: ошибка |
| 250. | 90400 | UserUISettingsChanged | Изменение UI настроек пользователя |
| 251. | 90500 | NodeAdded | Добавился узел |
| 252. | 90501 | NodeLost | Потерян узел |
| 253. | 90600 | LtwFileGroupCreated | Группа ltw-файлов создана |
| 254. | 90601 | LtwFileGroupChanged | Группа ltw-файлов изменена |
| 255. | 90602 | LtwFileGroupDeleted | Группа ltw-файлов удалена |
| 256. | 90700 | SelectorGroupCreated | Группа селекторов создана |
| 257. | 90701 | SelectorGroupChanged | Группа селекторов изменена |
| 258. | 90702 | SelectorGroupDeleted | Группа селекторов удалена |
| 259. | 90800 | LtwFileCreated | Ltw-файл создан |
| 260. | 90801 | LtwFileChanged | Ltw-файл изменен |
| 261. | 90802 | LtwFileDeleted | Ltw-файл удален |
| 262. | 90803 | LtwFileMovedToGroup | Ltw-файл перемещен в группу |
| 263. | 90900 | SelectorCreated | Селектор создан |
| 264. | 90901 | SelectorChanged | Селектор изменен |
| 265. | 90902 | SelectorDeleted | Селектор удален |
| 266. | 90903 | SelectorMovedToGroup | Селектор перемещен в группу |
| 267. | 91000 | AgentDistrUploaded | Закачан дистрибутив агента |
| 268. | 91001 | AgentDistrDeleted | Удален дистрибутив агента |
| 269. | 91099 | AgentUpdateStarted | AgentUpdate - Команда обновления запущена |
| 270. | 91100 | AgentUpdateStartedSuccess | AgentUpdate OK - Начало обновления |
| 271. | 91114 | AgentUpdateInstallerDownloadedSuccess | AgentUpdate OK - Скачивание инсталлятора |
| 272. | 91115 | AgentUpdateInstallerSavedSuccess | AgentUpdate OK - Сохранение инсталлятора |
| 273. | 91101 | AgentUpdateDistribDownloadedSuccess | AgentUpdate OK - Скачивание дистрибутива |
| 274. | 91102 | AgentUpdateDistribSavedSuccess | AgentUpdate OK - Сохранение дистрибутива |
| 275. | 91103 | AgentUpdateStartedAgentConsoleSuccess | AgentUpdate OK - Запуск AgentConsole в режиме обновления |
| 276. | 91104 | AgentUpdateStopedAgentServiceSuccess | AgentUpdate OK - Остановка сервиса агента |
| 277. | 91105 | AgentUpdateUpdatedAgentServiceSuccess | AgentUpdate OK - Обновление сервиса агента |
| 278. | 91106 | AgentUpdateStartedAgentServiceSuccess | AgentUpdate OK - Запуск сервиса агента |
| 279. | 91107 | AgentUpdateStartedError | AgentUpdate Error - Начало обновления |
| 280. | 91116 | AgentUpdateInstallerDownloadedError | AgentUpdate Error - Скачивание инсталлятора |
| 281. | 91117 | AgentUpdateInstallerSavedError | AgentUpdate Error - Сохранение инсталлятора |
| 282. | 91108 | AgentUpdateDistribDownloadedError | AgentUpdate Error - Скачивание дистрибутива |
| 283. | 91109 | AgentUpdateDistribSavedError | AgentUpdate Error - Сохранение дистрибутива |
| 284. | 91110 | AgentUpdateStartedAgentConsoleError | AgentUpdate Error - Запуск AgentConsole в режиме обновления |
| 285. | 91111 | AgentUpdateStopedAgentServiceError | AgentUpdate Error - Остановка сервиса агента |
| 286. | 91112 | AgentUpdateUpdatedAgentServiceError | AgentUpdate Error - Обновление сервиса агента |
| 287. | 91113 | AgentUpdateStartedAgentServiceError | AgentUpdate Error - Запуск сервиса агента |
| 288. | 91118 | AgentUpdateStartedAgentServiceFromBackupSuccess | AgentUpdate Success - Запуск сервиса агента из бэкапа |
| 289. | 91119 | AgentUpdateStartedAgentServiceFromBackupError | AgentUpdate Error - Запуск сервиса агента из бэкапа |
| 290. | 92000 | SecurityIncidentJournalAccessed | Просмотр журнала регистрации событий ИБ |
| 291. | 92100 | RdpUserPasswordChanged | Изменен пароль у RDP-пользователя |
| 292. | 91200 | PasswordPolicyEdited | Изменена политика паролей |
| 293. | 91201 | PasswordPolicyApplied | Применена политика паролей |

Список событий может быть изменен в следующих версиях Оркестратора.
