# Приложение 3 - События Оркестратора

:small_blue_diamond: В зависимости от используемой версии Оркестратора список событий может различаться.

Таблица 1 – Перечень событий Оркестратора

| № <p> п/п </p>| Код | Наименование | Описание |
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
| 11. | 109 | UserPasswordChangingFailed | Неудачная попытка изменить пароль у пользователя |
| 12. | 110 | UserPasswordChangingAttemptsLimitOut | Исчерпан лимит попыток изменения пароля |
| 13. | 2008 | LoginUserExpired | Срок действия учетной записи истек |
| 14. | 201 | RoleCreated | Роль создана |
| 15. | 202 | RoleChanged | Роль изменена |
| 16. | 203 | RoleDeleted | Роль удалена |
| 17. | 204 | RolePermissionsAssigned | Роли назначены права |
| 18. | 301 | WorkerCreated | Машина зарегистрирована |
| 19. | 302 | WorkerChanged | Машина изменена |
| 20. | 303 | WorkerDisabled | Машина выведена из эксплуатации |
| 21. | 304 | WorkerRebootStarted | Перезагрузка машины запущена |
| 22. | 305 | WorkerRebootCompleted | Перезагрузка машины завершена |
| 23. | 306 | WorkerTestAvailable | Машина доступна |
| 24. | 307 | WorkerTestNotAvailable | Машина недоступна |
| 25. | 308 | WorkerIpAddressSended | Машина робота отправила свой IP Оркестратору |
| 26. | 309 | WorkerLogOffAll | Разлогинивание всех RDP-пользователей |
| 27. | 310 | WorkerIncreaseLoading | На машине робота растет нагрузка |
| 28. | 311 | WorkerDecreaseLoading | На машине робота падает нагрузка |
| 29. | 312 | WorkerOverflowLoading | На машине робота нагрузка превышает допустимую |
| 30. | 401 | ProjectCreated | Проект создан |
| 31. | 402 | ProjectChanged | Проект изменен |
| 32. | 403 | ProjectDisabled | Проект выведен из эксплуатации |
| 33. | 404 | ProjectRun | Проект запущен |
| 34. | 405 | ProjectAddedRobot | К проекту добавлен робот |
| 35. | 406 | ProjectDeletedRobot | Из проекта/ов удален робот |
| 36. | 407 | ProjectChangedRobotOrder | Изменение приоритета роботов проекта |
| 37. | 408 | ProjectEnqueue | Проект добавлен в очередь выполнения |
| 38. | 410 | ProjectReEnqueue | Проект добавлен в очередь выполнения повторно |
| 39. | 409 | ProjectPeek | Проект извлечен из очереди выполнения |
| 40. | 411 | ProjectSwappedMainVersionUp | Проект назначен главной версией |
| 41. | 412 | ProjectSwappedMainVersionDown | Проект больше не является главной версией |
| 42. | 413 | ProjectVersionCreated | Версия проекта создана |
| 43. | 414 | ProjectDeletedFromQueue | Проект удален из очереди на выполнение |
| 44. | 415 | ProjectDownloaded | Скачан архив проекта |
| 45. | 417 | ProjectVariablesChanged | Переменные проекта изменены |
| 46. | 418 | ProjectArchiveIdRequested | ProjectArchiveId запрошен агентом |
| 47. | 416 | ProjectArchiveUploaded | Архив проекта загружен |
| 48. | 419 | ProjectTagsAdded | К проекту добавлены теги |
| 49. | 420 | ProjectTagsDeleted | У проекта удалены теги |
| 50. | 421 | ProjectNotEnqueue | Проект не добавлен в очередь выполнения |
| 51. | 422 | ProjectRobotServiceBreakAssignmentNotAllowOverlay | Проект запущен по заданию и еще не завершен (RobotService) |
| 52. | 423 | ProjectRobotServiceBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (RobotService) |
| 53. | 424 | ProjectRobotStartBreakAssignmentNotAllowOverlay | Проект запущен по заданию и еще не завершен (RobotStart) |
| 54. | 425 | ProjectRobotStartBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (RobotStart) |
| 55. | 426 | ProjectQueueBreakProjectLimitedLaunch | Проект запущен в максимальном количестве экземпляров (Queue) |
| 56. | 501 | RobotCreated | Робот зарегистрирован |
| 57. | 502 | RobotDisabled | Робот выведен из эксплуатации |
| 58. | 503 | RobotDeployStarted | Развертывание робота запущено |
| 59. | 504 | RobotStartStarted | Старт робота запущен |
| 60. | 505 | RobotStartCompleted | Старт робота завершен |
| 61. | 506 | RobotEraseStarted | Стирание робота запущено |
| 62. | 507 | RobotEraseCompleted | Стирание робота завершено |
| 63. | 508 | RobotProjectRun | Проект на роботе запущен |
| 64. | 509 | RobotProjectStopped | Проект на роботе остановлен |
| 65. | 510 | RobotDeployCompleted | Развертывание робота завершено |
| 66. | 511 | RobotStartError | Ошибка при запуске робота |
| 67. | 512 | RobotProjectCompletedSuccess | Зафиксировано удачное завершение выполнения проекта роботом |
| 68. | 513 | RobotProjectCompletedError | Зафиксировано неудачное завершение выполнения проекта роботом |
| 69. | 514 | RobotHardKillStarted | Старт принудительной остановки робота |
| 70. | 515 | RobotHardKillCompleted | Принудительная остановка робота завершена |
| 71. | 516 | RobotSoftKillStarted | Старт мягкой остановки робота |
| 72. | 517 | RobotSoftKillCompleted | Мягкая остановка робота завершена |
| 73. | 518 | RobotStartedFromAssignment | Робот запущен из задания |
| 74. | 519 | RobotUnavailableRDPLogOff | Робот недоступен - RDPLogOff |
| 75. | 520 | RobotStartedFromAssignmentError | Ошибка запуска робота из задания |
| 76. | 521 | RobotManualAgentUnlocked | Ручная разблокировка робота, заблокированного агентом |
| 77. | 522 | RobotDeletedProject | У робота удален проект/ы |
| 78. | 523 | RobotManualAgentUnlockedError | Ошибка ручной разблокировки робота, заблокированного агентом |
| 79. | 601 | LicenseAdded | Лицензия добавлена |
| 80. | 602 | LicenseDeleted | Лицензия удалена |
| 81. | 603 | LicenseDownloaded | Лицензия скачана |
| 82. | 604 | LicenseRevoked | Лицензия отозвана |
| 83. | 605 | LicenseRevokeReplaced | Отозванная лицензия заменена |
| 84. | 606 | LicenseRequested | Создан запрос на новую лицензию |
| 85. | 607 | LicenseReplaceRequested | Создан запрос на замен лицензии |
| 86. | 608 | LicenseTakeAvailableRobotOk | Робот занял свободную лицензию |
| 87. | 609 | LicenseTakeAvailableRobotError | Ошибка занятия лицензии роботом |
| 88. | 610 | LicenseRobotReleaseOk | Лицензия робота освобождена |
| 89. | 611 | LicenseRobotReleaseError | Ошибка освобождения лицензии робота |
| 90. | 612 | LicenseToTenantAdded | Лицензия выдана на тенант |
| 91. | 613 | LicenseTakeAvailableStudioOk | Студия заняла свободную лицензию |
| 92. | 614 | LicenseTakeAvailableStudioError | Ошибка занятия лицензии студией |
| 93. | 615 | LicenseStudioTimeoutRelease | Лицензия студии освобождена по таймауту |
| 94. | 616 | LicenseRobotTimeoutRelease | Лицензия робота освобождена по таймауту |
| 95. | 617 | LicenseTakeAvailableAttendedRobotOk | Аттендед робот занял свободную лицензию |
| 96. | 618 | LicenseTakeAvailableAttendedRobotError | Ошибка занятия лицензии аттендед роботом |
| 97. | 619 | LicenseAttendedRobotReleaseOk | Лицензия аттендед робота освобождена |
| 98. | 620 | LicenseAttendedRobotReleaseError | Ошибка освобождения лицензии аттендед робота |
| 99. | 621 | LicenseDeactivated | Лицензия деактивирована |
| 100. | 622 | LicenseActivated | Лицензия активирована после деактивации |
| 101. | 701 | AssetCreated | Ресурс создан |
| 102. | 702 | AssetChanged | Ресурс изменен |
| 103. | 703 | AssetDeleted | Ресурс удален |
| 104. | 801 | DeployTemplateCreated | Шаблон развертывания создан |
| 105. | 802 | DeployTemplateChanged | Шаблон развертывания изменен |
| 106. | 803 | DeployTemplateDisabled | Шаблон развертывания выведен из эксплуатации |
| 107. | 1201 | RobotDistrUploaded | Дистрибутив робота загружен |
| 108. | 1202 | RobotDistrActivated | Дистрибутив робота активирован |
| 109. | 1203 | RobotDistrDeleted | Дистрибутив робота удален |
| 110. | 1204 | NodesDesynchronization | Рассинхронизация дистрибутива робота на узлах |
| 111. | 1205 | NodeSequentialSwitching | Мерцание согласования дистрибутива робота на узле |
| 112. | 2001 | Login | Пользователь авторизовался |
| 113. | 2002 | LoginUserNotExist | Пользователь не существует |
| 114. | 2003 | LoginUserLocked | Пользователь заблокирован |
| 115. | 2004 | LoginUserUnauthorized | Ошибка авторизации |
| 116. | 2005 | LoginUserUnauthorizedAD | Ошибка авторизации в AD |
| 117. | 2006 | LoginUserNoRightsGroupAD | Группа AD не имеет привязки к роли |
| 118. | 2007 | LogOut | Пользователь вышел из системы |
| 119. | 3001 | ExchangeQueueCreated | Очередь обмена для роботов создана |
| 120. | 3002 | ExchangeQueueChanged | Очередь обмена для роботов изменена |
| 121. | 3003 | ExchangeQueueDeleted | Очередь обмена для роботов удалена |
| 122. | 3004 | ExchangeQueuePermissionsAssigned | Очередь обмена для роботов - назначены права |
| 123. | 3005 | ExchangeQueueEnqueue | Очередь обмена для роботов - добавление значения |
| 124. | 3006 | ExchangeQueuePeek | Очередь обмена для роботов - извлечение значения |
| 125. | 3007 | ExchangeQueueReadedByKey | Очередь обмена для роботов - чтение значения по ключу |
| 126. | 3008 | ExchangeQueueRemovedByKey | Очередь обмена для роботов - удаление значения по ключу |
| 127. | 3009 | ExchangeQueueChangeStatusByKey | Очередь обмена для роботов - изменение статуса элемента по ключу |
| 128. | 3010 | ExchangeQueueReEnqueue | Очередь обмена для роботов - повторное помещение элемента в очередь |
| 129. | 3011 | ExchangeQueueAddMetadataByKey | Очередь обмена для роботов - добавление метаданных к элементу по ключу |
| 130. | 3012 | ExchangeQueueReadedItems | Очередь обмена для роботов - чтение элементов по фильтру |
| 131. | 3013 | ExchangeQueueItemTagsAdded | Очередь обмена для роботов - добавление тегов к элементу |
| 132. | 3014 | ExchangeQueueItemTagsDeleted | Очередь обмена для роботов - удаление тегов у элемента |
| 133. | 3015 | ExchangeQueueAddTagsByKey | Очередь обмена для роботов - добавление тегов к элементу по ключу |
| 134. | 3016 | ExchangeQueueEnqueueFromOrchestrator | Очередь обмена для роботов - добавление элемента из оркестратора |
| 135. | 3017 | ExchangeQueueItemChangedFromOrchestrator | Очередь обмена для роботов - изменение элемента из оркестратора |
| 136. | 3018 | ExchangeQueueItemDeletedFromOrchestrator | Очередь обмена для роботов - удаление элемента из оркестратора |
| 137. | 3019 | ExchangeQueueItemClonedFromOrchestrator | Очередь обмена для роботов - клонирование элемента из оркестратора |
| 138. | 3020 | ExchangeQueueItemRepeatedFromOrchestrator | Очередь обмена для роботов - повторение элемента из оркестратора |
| 139. | 3021 | ExchangeQueueEditValueByKey | Очередь обмена для роботов - изменение значения элемента |
| 140. | 3022 | ExchangeQueueReadedItemsWithLock | Очередь обмена для роботов - чтение элементов по фильтру с блокировкой |
| 141. | 3023 | ExchangeQueueUnlockItems | Очередь обмена для роботов - снятие блокировки с элементов |
| 142. | 3024 | ExchangeQueueReadedByKeyWithLock | Очередь обмена для роботов - чтение элемента по ключу с блокировкой |
| 143. | 4001 | RobotGroupCreated | Группа роботов создана |
| 144. | 4002 | RobotGroupChanged | Группа роботов изменена |
| 145. | 4003 | RobotGroupDeleted | Группа роботов удалена |
| 146. | 4004 | RobotGroupAddedRobots | В группу роботов добавлены роботы |
| 147. | 4005 | RobotGroupDeletedRobots | Из группы роботов удалены роботы |
| 148. | 5000 | ProjectQueuePurged | Очередь проектов очищена |
| 149. | 5001 | ProjectQueueItemDeleted | Очередь проектов - удален элемент |
| 150. | 6000 | ScheduleCreated | Расписание создано |
| 151. | 6001 | ScheduleChanged | Расписание изменено |
| 152. | 6002 | ScheduleDeleted | Расписание удалено |
| 153. | 7001 | AgentDeployTrackingStart | Разворачивание робота - Процесс запущен |
| 154. | 7010 | AgentDeployTrackingCopyingRobotDistr | Разворачивание робота - Скачивание дистрибутива Робота с Оркестратора |
| 155. | 7011 | AgentDeployTrackingSaveRobotDistr | Разворачивание робота - Сохранение дистрибутива Робота на машине Робота |
| 156. | 7020 | AgentDeployTrackingKillRobotProcess | Разворачивание робота - Уничтожение процесса Робота, если такой есть запущенный |
| 157. | 7030 | AgentDeployTrackingUnpackRobotDistr | Разворачивание робота - Распаковка дистрибутива Робота |
| 158. | 7040 | AgentDeployTrackingImportingSSLCert | Разворачивание робота - Импорт ssl-сертификата из дистрибутива Робота в хранилище сертификатов ОС |
| 159. | 7050 | AgentDeployTrackingTransforRobotConfig | Разворачивание робота - Трансформация конфига Робота под параметры деплоя |
| 160. | 7060 | AgentDeployTrackingReservationUrlWithOrchPort | Разворачивание робота - Резервирование url+port для https-службы Робота с port, переданным Оркестратором |
| 161. | 7061 | AgentDeployTrackingReservationUrlWithActualPort | Разворачивание робота - url зарезервирован для port, резервировать с первым свободным после переданного port |
| 162. | 7070 | AgentDeployTrackingBindingSSLCertToRobotService | Разворачивание робота - Привязка ssl-сертификата к службе робота |
| 163. | 8001 | AgentStartRobotTrackingStart | Старт робота - Процесс запущен |
| 164. | 8010 | AgentStartRobotTrackingDownloadProjectArch | Старт робота - Скачивание архива проекта с Оркестратора |
| 165. | 8011 | AgentStartRobotTrackingSaveProjectArch | Старт робота - Сохранение архива проекта на машине Робота |
| 166. | 8020 | AgentStartRobotTrackingKillRobotProcess | Старт робота - Уничтожение процесса Робота, если такой есть запущенный |
| 167. | 8021 | AgentStartRobotTrackingGenerateRunScript | Старт робота - Генерация скрипта запуска Робота |
| 168. | 8022 | AgentStartRobotTrackingCreateTaskToStartRobot | Старт робота - Создание Windows Task запуска Робота (для Windows 2016 Server) |
| 169. | 8023 | AgentStartRobotTrackingDirectlyStartRobot | Старт робота - Непосредственный запуск Робота |
| 170. | 8030 | AgentStartRobotTrackingWaitStartRobot | Старт робота - Ожидание старта приложения Робота |
| 171. | 8031 | AgentStartRobotTrackingTakeAvailableRobotLicense | Старт робота - Робот получил свободную лицензию |
| 172. | 8040 | AgentStartRobotWaitExecuteWorkflow | Старт робота - Ожидание выполнения проекта Роботом |
| 173. | 8050 | AgentStartRobotTrackingExecuteWorkflow | Старт робота - Проект запущен |
| 174. | 9000 | AssignmentCreated | Задание создано |
| 175. | 9001 | AssignmentChanged | Задание изменено |
| 176. | 9002 | AssignmentDeleted | Задание удалено |
| 177. | 9010 | AssignmentProjectQueued | Проект задания поставлен в очередь выполнения |
| 178. | 9011 | AssignmentProjectQueuedError | Ошибка постановки проекта задания в очередь выполнения |
| 179. | 9012 | AssignmentStarted | Задание запущено |
| 180. | 9013 | AssignmentPaused | Задание остановлено |
| 181. | 9014 | AssignmentResumed | Задание возобновлено |
| 182. | 9015 | AssignmentCompleted | Задание выполнено |
| 183. | 9016 | AssignmentIncreaseTriggerNativeEventBus | Увеличение очереди событий от триггеров |
| 184. | 9017 | AssignmentDecreaseTriggerNativeEventBus | Уменьшение очереди событий от триггеров |
| 185. | 9018 | AssignmentOverflowTriggerNativeEventBus | Переполнение очереди событий от триггеров |
| 186. | 10000 | RpaProjectQueueProcessingTypeChanged | Параметры обработки очереди на выполнение проектов изменены |
| 187. | 20000 | LogsTruncate | Очистка логов |
| 188. | 20001 | LogsDumpStarted | Выгрузка логов запущена |
| 189. | 20002 | LogsDumpCompleted | Выгрузка логов завершена |
| 190. | 30001 | ProductionCalendarsCreated | Создание производственного календаря |
| 191. | 30002 | ProductionCalendarsChanged | Изменение производственного календаря |
| 192. | 30003 | ProductionCalendarsDeleted | Удаление производственного календаря |
| 193. | 40001 | AgentCreated | Агент создан |
| 194. | 40002 | AgentChanged | Агент изменен |
| 195. | 40003 | AgentDeleted | Агент удален |
| 196. | 40004 | AgentTestAvailable | Агент доступен |
| 197. | 40005 | AgentTestNotAvailable | Агент недоступен |
| 198. | 40006 | AgentEnabledKeepRDPSession | RDP - EnabledKeepRDPSession |
| 199. | 40007 | AgentDisabledKeepRDPSession | RDP - DisabledKeepRDPSession |
| 200. | 40008 | AgentEnabledKeepRDPSessionError | RDP - EnabledKeepRDPSessionError |
| 201. | 40009 | AgentLogOffStarted | RDP - LogOffStarted |
| 202. | 40010 | AgentLogOffCompletedSuccess | RDP - LogOffCompletedSuccess |
| 203. | 40011 | AgentLogOffCompletedError | RDP - LogOffCompletedError |
| 204. | 40012 | AgentMaxAttemptStartLogOff | RDP - MaxAttemptStartLogOff |
| 205. | 40013 | AgentMaxAttemptLogOff | RDP - MaxAttemptLogOff |
| 206. | 40016 | AgentConnectedFlickers | Мерцание RDP-сессии |
| 207. | 50001 | TenantCreated | Тенант создан |
| 208. | 50002 | TenantChanged | Тенант изменен |
| 209. | 50003 | TenantDisabled | Тенант выведен из эксплуатации |
| 210. | 60001 | TriggerScheduleFired | Сработал триггер расписания |
| 211. | 60002 | TriggerEmailFired | Сработал триггер Email |
| 212. | 60003 | TriggerExchangeQueueFired | Сработал триггер очереди обмена данными |
| 213. | 60004 | TriggerFolderFired | Сработал триггер папки |
| 214. | 60005 | TriggerProjectCompletedFired | Сработал триггер завершения проекта |
| 215. | 60006 | TriggerFromRobotFired | Сработал триггер запуска задания из робота |
| 216. | 70001 | IncomingEmailCreated | Создание Email для входящей почты |
| 217. | 70002 | IncomingEmailChanged | Изменение Email для входящей почты |
| 218. | 70003 | IncomingEmailDeleted | Удаление Email для входящей почты |
| 219. | 80001 | FolderCreated | Создание личной папки |
| 220. | 80002 | FolderChanged | Изменение личной папки |
| 221. | 80003 | FolderDeleted | Удаление личной папки |
| 222. | 80004 | FolderResubordination | Переподчинение личной папки |
| 223. | 80005 | FolderMoveObjects | Перемещение объектов в личную папку |
| 224. | 80006 | FolderMissingProject | Проект отсутствует в личной папке |
| 225. | 80007 | FolderMissingRobots | В личной папке отсутствуют роботы |
| 226. | 80021 | Folder2Created | Создание папки |
| 227. | 80022 | Folder2Changed | Изменение папки |
| 228. | 80023 | Folder2Deleted | Удаление папки |
| 229. | 80024 | Folder2Resubordination | Переподчинение папки |
| 230. | 80025 | Folder2MoveObjects | Перемещение объектов в папку |
| 231. | 80026 | Folder2MissingProject | Проект отсутствует в папке |
| 232. | 80027 | Folder2MissingRobots | В папке отсутствуют роботы |
| 233. | 80028 | Folder2GrantOrchUserFolders | Оркестраторному пользователю изменены права на папки |
| 234. | 80029 | Folder2GrantFolderUsers | На папку пользователям изменены права |
| 235. | 90001 | GrantUserWorker | Предоставление пользователю машина робота |
| 236. | 90002 | GrantUserWorkerCanceled | Предоставление пользователю машина робота отменено |
| 237. | 90003 | GrantUserAgent | Предоставление пользователю агента |
| 238. | 90004 | GrantUserAgentCanceled | Предоставление пользователю агента отменено |
| 239. | 90101 | UserGrantCreated | Наследование объектов создано |
| 240. | 90102 | UserGrantChanged | Наследование объектов изменено |
| 241. | 90103 | UserGrantDeleted | Наследование объектов удалено |
| 242. | 90201 | NuGetPackageUploaded | NuGet: пакет закачан в папку оркестратора |
| 243. | 90202 | NuGetPackagePublishStarted | NuGet: публикация пакета запущена |
| 244. | 90203 | NuGetPackagePublishCompletedOk | NuGet: публикация пакета завершена |
| 245. | 90204 | NuGetPackagePublishCompletedError | NuGet: ошибка при публикация пакета |
| 246. | 90205 | NuGetPackageRemoveStarted | NuGet: удаление пакета запущено |
| 247. | 90206 | NuGetPackageRemoveCompletedOk | NuGet: удаление пакета завершено |
| 248. | 90207 | NuGetPackageRemoveCompletedError | NuGet: ошибка при удалении пакета |
| 249. | 90300 | RpaProjectLaunchLogsTransferSuccess | Перенос старых запусков в БД с логами: успешно |
| 250. | 90301 | RpaProjectLaunchLogsTransferError | Перенос старых запусков в БД с логами: ошибка |
| 251. | 90400 | UserUISettingsChanged | Изменение UI настроек пользователя |
| 252. | 90500 | NodeAdded | Добавился узел |
| 253. | 90501 | NodeLost | Потерян узел |
| 254. | 90600 | LtwFileGroupCreated | Группа ltw-файлов создана |
| 255. | 90601 | LtwFileGroupChanged | Группа ltw-файлов изменена |
| 256. | 90602 | LtwFileGroupDeleted | Группа ltw-файлов удалена |
| 257. | 90700 | SelectorGroupCreated | Группа селекторов создана |
| 258. | 90701 | SelectorGroupChanged | Группа селекторов изменена |
| 259. | 90702 | SelectorGroupDeleted | Группа селекторов удалена |
| 260. | 90800 | LtwFileCreated | Ltw-файл создан |
| 261. | 90801 | LtwFileChanged | Ltw-файл изменен |
| 262. | 90802 | LtwFileDeleted | Ltw-файл удален |
| 263. | 90803 | LtwFileMovedToGroup | Ltw-файл перемещен в группу |
| 264. | 90900 | SelectorCreated | Селектор создан |
| 265. | 90901 | SelectorChanged | Селектор изменен |
| 266. | 90902 | SelectorDeleted | Селектор удален |
| 267. | 90903 | SelectorMovedToGroup | Селектор перемещен в группу |
| 268. | 91000 | AgentDistrUploaded | Закачан дистрибутив агента |
| 269. | 91001 | AgentDistrDeleted | Удален дистрибутив агента |
| 270. | 91099 | AgentUpdateStarted | AgentUpdate - Команда обновления запущена |
| 271. | 91100 | AgentUpdateStartedSuccess | AgentUpdate OK - Начало обновления |
| 272. | 91114 | AgentUpdateInstallerDownloadedSuccess | AgentUpdate OK - Скачивание инсталлятора |
| 273. | 91115 | AgentUpdateInstallerSavedSuccess | AgentUpdate OK - Сохранение инсталлятора |
| 274. | 91101 | AgentUpdateDistribDownloadedSuccess | AgentUpdate OK - Скачивание дистрибутива |
| 275. | 91102 | AgentUpdateDistribSavedSuccess | AgentUpdate OK - Сохранение дистрибутива |
| 276. | 91103 | AgentUpdateStartedAgentConsoleSuccess | AgentUpdate OK - Запуск AgentConsole в режиме обновления |
| 277. | 91104 | AgentUpdateStopedAgentServiceSuccess | AgentUpdate OK - Остановка сервиса агента |
| 278. | 91105 | AgentUpdateUpdatedAgentServiceSuccess | AgentUpdate OK - Обновление сервиса агента |
| 279. | 91106 | AgentUpdateStartedAgentServiceSuccess | AgentUpdate OK - Запуск сервиса агента |
| 280. | 91107 | AgentUpdateStartedError | AgentUpdate Error - Начало обновления |
| 281. | 91116 | AgentUpdateInstallerDownloadedError | AgentUpdate Error - Скачивание инсталлятора |
| 282. | 91117 | AgentUpdateInstallerSavedError | AgentUpdate Error - Сохранение инсталлятора |
| 283. | 91108 | AgentUpdateDistribDownloadedError | AgentUpdate Error - Скачивание дистрибутива |
| 284. | 91109 | AgentUpdateDistribSavedError | AgentUpdate Error - Сохранение дистрибутива |
| 285. | 91110 | AgentUpdateStartedAgentConsoleError | AgentUpdate Error - Запуск AgentConsole в режиме обновления |
| 286. | 91111 | AgentUpdateStopedAgentServiceError | AgentUpdate Error - Остановка сервиса агента |
| 287. | 91112 | AgentUpdateUpdatedAgentServiceError | AgentUpdate Error - Обновление сервиса агента |
| 288. | 91113 | AgentUpdateStartedAgentServiceError | AgentUpdate Error - Запуск сервиса агента |
| 289. | 91118 | AgentUpdateStartedAgentServiceFromBackupSuccess | AgentUpdate Success - Запуск сервиса агента из бэкапа |
| 290. | 91119 | AgentUpdateStartedAgentServiceFromBackupError | AgentUpdate Error - Запуск сервиса агента из бэкапа |
| 291. | 92000 | SecurityIncidentJournalAccessed | Просмотр журнала регистрации событий ИБ |
| 292. | 92100 | RdpUserPasswordChanged | Изменен пароль у RDP-пользователя |
| 293. | 91200 | PasswordPolicyEdited | Изменена политика паролей |
| 294. | 91201 | PasswordPolicyApplied | Применена политика паролей |

Список событий может быть изменен в следующих версиях Оркестратора.