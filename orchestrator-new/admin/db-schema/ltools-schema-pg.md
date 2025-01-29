# **Описание структуры БД ltools**

## \_\_EFMigrationsHistory

Системная[1] таблица с миграциями

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>MigrationId</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ProductVersion</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## Agents

RDP-пользователи[2]

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 25%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 43%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AdminName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Логин RDP-пользователя. Не обязательно администратора. Учетка, под
которой запускается робот для варианта удержания RDP-сессии для случая
удержания RDP-сессий внешней службой. Должен совпадать с
локальной/доменной учеткой RDP-пользователя</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>AdminPassword</td>
<td>YES</td>
<td>nvarchar</td>
<td>Пароль RDP-пользователя</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>WorkerId</td>
<td>NO</td>
<td>int</td>
<td>Машина робота (FK)</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Notificated</td>
<td>YES</td>
<td>bit</td>
<td>Не используется. Оставлено для совместимости со старыми
версиями</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>KeepRDPSession</td>
<td>NO</td>
<td>bit</td>
<td>Поддерживать активной RDP-сессию. Флаг устанавливается вручную в
Оркестраторе, или при запуске робота автоматически, если робот развернут
под RDP-пользователем.</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Connected</td>
<td>NO</td>
<td>bit</td>
<td>Признак, что RDP-сессия активна</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>ConnectedChangedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения состояния RDP-сессии, например
отключилась/подключилась</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ConnectedUpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата обновления состояния RDP-сессии при периодическом опросе для её
поддержания. Не обязательно переключение типа отключилась/подключилась,
дата срабатывания периодического опроса</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>AuthenticationLevel</td>
<td>NO</td>
<td>int</td>
<td>RDP-параметр<a href="#fn1" class="footnote-ref" id="fnref1"
role="doc-noteref"><sup>1</sup></a></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>ColorDepth</td>
<td>NO</td>
<td>int</td>
<td>RDP-параметр</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>DesktopHeight</td>
<td>NO</td>
<td>int</td>
<td>RDP-параметр</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>DesktopWidth</td>
<td>NO</td>
<td>int</td>
<td>RDP-параметр</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>EnableCredSspSupport</td>
<td>NO</td>
<td>bit</td>
<td>RDP-параметр</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>NegotiateSecurityLayer</td>
<td>NO</td>
<td>bit</td>
<td>RDP-параметр</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>RdpPort</td>
<td>YES</td>
<td>int</td>
<td>Специфический (отличается от по умолчанию) порт для RDP</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>NeedForLogOff</td>
<td>NO</td>
<td>bit</td>
<td>Сигнал разлогинить пользователя после закрытия его RDP-сессии.
Отключение RDP-сессии не разлогинивает пользователя, занятые им ресурсы
удерживаются. Этот сигнал позволяет Оркестратору именно разлогинить
пользователя, что освободит занятые пользователем ресурсы</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>LogOffStartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата старта команды разлогона RDP-пользователя</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>LogOffCompletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата завершения команды разлогона RDP-пользователя</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>LogOffSuccess</td>
<td>YES</td>
<td>bit</td>
<td>Результат завершения команды разлогона RDP-пользователя</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>AttemptLogOff</td>
<td>NO</td>
<td>int</td>
<td>Попытка разлогона</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>AttemptStartLogOff</td>
<td>NO</td>
<td>int</td>
<td>Попытка отправки команды разлогона в Агент</td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>ConnectedFlickersCount</td>
<td>NO</td>
<td>int</td>
<td>Счетчик постоянных переключений (на основе сравнения
ConnectedChangedAt и текущей даты, разность задается в конфиге).; Если
доходит до некоторого значения (задается в конфиге), является признаком
мерцания RDP-сессии.; Тогда устанавливается флаг ConnectedFlickers</td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>ConnectedFlickers</td>
<td>NO</td>
<td>bit</td>
<td>Флаг мерцания RDP-сессии. По этому флагу выбираются мерцающие
RDP-сессии для виджета на главной</td>
</tr>
<tr class="odd">
<td><ol start="25" type="1">
<li></li>
</ol></td>
<td>UserProfileLoaded</td>
<td>NO</td>
<td>bit</td>
<td>Признак загрузки профиля пользователя. Если сессия открылась, еще
может не прогрузиться профиль; (с AD-пользователями это иногда занимает
много времени). А без прогруженного профиля работать не будет; запуск
Windows-task (75%)</td>
</tr>
<tr class="even">
<td><ol start="26" type="1">
<li></li>
</ol></td>
<td>NodeId</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, которая меняла запись</td>
</tr>
</tbody>
</table>
<section id="footnotes" class="footnotes footnotes-end-of-document"
role="doc-endnotes">
<hr />
<ol>
<li id="fn1"><p>Здесь и далее из документации к библиотеке подключения<a
href="#fnref1" class="footnote-back" role="doc-backlink">↩︎</a></p></li>
</ol>
</section>

## Assets

Ресурс робота, централизованно хранящийся в Оркестраторе. Робот/Студия
может писать/читать ресурс

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 32%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование ресурса. При использовании равносильно имени
переменной</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td>Значение (зашифрованное)</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>ValueType</td>
<td>NO</td>
<td>int</td>
<td>Тип значения</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>YES</td>
<td>int</td>
<td>Робот-владелец (FK). Если не NULL, только робот-владелец имеет
доступ<a href="#fn1" class="footnote-ref" id="fnref1"
role="doc-noteref"><sup>1</sup></a></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Readonly</td>
<td>NO</td>
<td>bit</td>
<td>Флаг только для чтения</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание ресурса</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>CyberArkAccountId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор аккаунта</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>CyberArkActionType</td>
<td>YES</td>
<td>nvarchar</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>CyberArkIsUse</td>
<td>YES</td>
<td>bit</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>CyberArkMachine</td>
<td>YES</td>
<td>nvarchar</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>CyberArkReason</td>
<td>YES</td>
<td>nvarchar</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>CyberArkTicketId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>CyberArkTicketingSystemName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>CyberArkVersion</td>
<td>YES</td>
<td>int</td>
<td>Тип хранилища CyberArk (устар.)</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>ExtStoreType</td>
<td>YES</td>
<td>int</td>
<td>Тип внешнего хранилища</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>LockTimeout</td>
<td>YES</td>
<td>int</td>
<td>Таймаут (сек) блокировки</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>LockType</td>
<td>YES</td>
<td>int</td>
<td>Тип блокировки</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>RobotLockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата блокировки</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>RobotLockId</td>
<td>YES</td>
<td>int</td>
<td>Заблокировавший робот</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>RobotLockUserId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Заблокировавший аттендед-робот</td>
</tr>
</tbody>
</table>
<section id="footnotes" class="footnotes footnotes-end-of-document"
role="doc-endnotes">
<hr />
<ol>
<li id="fn1"><p>Устаревшее. Связь с роботами через таблицу AssetRobots<a
href="#fnref1" class="footnote-back" role="doc-backlink">↩︎</a></p></li>
</ol>
</section>

## AssetRobots

Назначение ресурсов отдельным роботам. Только эти роботы (и студия)
имеют доступ к ресурсам

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 12%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>YES</td>
<td>int</td>
<td>Робот-владелец (FK). Если не NULL, только робот-владелец имеет
доступ</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>AssetId</td>
<td>NO</td>
<td>bit</td>
<td>Флаг только для чтения</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Key</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## Assignments

Задания (для автоматического запуска проектов на роботах)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 34%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Подробное описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>RpaProjectId</td>
<td>NO</td>
<td>int</td>
<td>RPA-проект (FK)</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>ScheduleId</td>
<td>YES</td>
<td>int</td>
<td>Не используется</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>LockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Системное</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>NO</td>
<td>int</td>
<td>Системное</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>NodeLock</td>
<td>YES</td>
<td>int</td>
<td>Системное</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Signal</td>
<td>YES</td>
<td>int</td>
<td>Системное</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>SignalCreatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Системное</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>StartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата запуска задания. Не робота по задания, а именно задания.
Альтернатива – задание не запущено</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>Status</td>
<td>NO</td>
<td>int</td>
<td><p>Состояние задания (enum).</p>
<p>New = 0, Running = 1,Complete = 2, Paused = 3</p></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>FiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания триггера (одного из многих) задания</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>NextFiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Следующая дата срабатывания триггера. Только для периодических
триггеов</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>StateChangedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения состояния задания</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>CountRobots</td>
<td>YES</td>
<td>int</td>
<td>Количество роботов, которые одновременно запустятся по заданию. По
умолчанию – один</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>WithTriggers</td>
<td>YES</td>
<td>bit</td>
<td>Флаг (избыточен, оптимизация), что задание с триггерами. Иначе
задание с ручным запуском</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>AutomaticApplyActiveRpaProject</td>
<td>NO</td>
<td>bit</td>
<td>Если у проекта задания изменится признак активности, автоматически
будет в задании использоваться активная версия проекта</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>AllowOverlay</td>
<td>NO</td>
<td>bit</td>
<td>Разрешить наложение</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>IsMassOperation</td>
<td>YES</td>
<td>bit</td>
<td>Задание остановлено в результате массовой операции:; True - да (и
статус Пауза ); False - нет; null - для совместимости с версией, где
триггеров еще нет</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>UserFolderId</td>
<td>NO</td>
<td>int</td>
<td>Папка пользователя, в контексте которой произощло событие; Для
кэширования списка Id роботов папки</td>
</tr>
</tbody>
</table>

## AssignmentSchedulerSignalNodeConfirms

Системная таблица. Запросы к ней не рекомендуются, за исключением особых
случаев разбора ошибок, согласованных с Вендором

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 23%" />
<col style="width: 18%" />
<col style="width: 17%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор ноды WebApi</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Confirm</td>
<td>NO</td>
<td>bit</td>
<td>Подтверждение</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления записи</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## AssignmentVariables

Привязка переменных проекта к заданию

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 16%" />
<col style="width: 12%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>NO</td>
<td>int</td>
<td>Задание (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RpaProjectVariableId</td>
<td>NO</td>
<td>int</td>
<td>Проект (FK)</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td>Значение, которое имеет переменная проекта на задании</td>
</tr>
</tbody>
</table>

## BlackWhiteIpStudioRules

Запись ЧБ списка IP-шников для запуска Primo.Studio

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 43%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ChangedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения записи</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>ComputerNameMask</td>
<td>YES</td>
<td>nvarchar</td>
<td>Маски имен машин</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>IpAddressFromId</td>
<td>YES</td>
<td>int</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>IpAddressMaskId</td>
<td>YES</td>
<td>int</td>
<td>-</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>IpAddressToId</td>
<td>YES</td>
<td>int</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>IsWhiteRule</td>
<td>NO</td>
<td>bit</td>
<td>Разрешено (правило из белого списка)</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>RuleType</td>
<td>NO</td>
<td>int</td>
<td>Тип ЧБ правила: диапазн IP адресов, IP маска подсети или маска имен
машин</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
</tbody>
</table>

## BusyRobotLicenseItems

Системная таблица. Для оптимизации. Использовать нельзя

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>RobotKey</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
</tbody>
</table>

## BusyRobotLicenses

Системная таблица. Использовать нельзя

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 17%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td>Зашифроанный json с массивом занятых лицензий</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Служебное поле для разруливания конкурентного доступа</td>
</tr>
</tbody>
</table>

## BusyStudioLicenses

Системная таблица. Использовать нельзя

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## ConfigHash

Системная таблица. Использовать нельзя

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 18%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>NO</td>
<td>nvarchar</td>
<td>Идентификатор ноды WebApi</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Hash</td>
<td>NO</td>
<td>nvarchar</td>
<td>Вычисляется на основе конкатенации всех файлов конфига в алфавитном
порядке</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>PreviousHash</td>
<td>YES</td>
<td>nvarchar</td>
<td>Прошлое значение Hash</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения. Устанавливается, если с прошлого запуска хэш
изменился. Является инцедентом безопасности</td>
</tr>
</tbody>
</table>

## CurrentSystemParameters

Системная таблица. Использовать нельзя

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 32%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>DateTimeValue</td>
<td>YES</td>
<td>nvarchar</td>
<td>Текущее системное время</td>
</tr>
</tbody>
</table>

## DeployTemplates

Шаблон развертывания робота

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 17%" />
<col style="width: 13%" />
<col style="width: 41%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>NoConsole</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>LogToFile</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>LogCustomToFile</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>LogMessageTypes</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>LogFormat</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>ThreadsCount</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ThreadStartIndex</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>ThrPriority</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>AppPriority</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>MinThreads</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>StartupPosition</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>DebugOptions</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>Disabled</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>LogInterval</td>
<td>YES</td>
<td>int</td>
<td>Интервал отправки лога в оркестратор (мсек)</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>LogPackSize</td>
<td>YES</td>
<td>int</td>
<td>Размер пачки лога</td>
</tr>
</tbody>
</table>

## ExchangeQueueRobotPermissions

Права робота на очередь обмена данными. Если задано, права определяются
по этой таблице

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 23%" />
<col style="width: 18%" />
<col style="width: 18%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Очередь обмена данными (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td>Робот (FK)</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Read</td>
<td>NO</td>
<td>bit</td>
<td>Можно читать</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Write</td>
<td>NO</td>
<td>bit</td>
<td>Можно писать</td>
</tr>
</tbody>
</table>

## ExchangeQueues

Очередь обмена данными

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 33%" />
<col style="width: 12%" />
<col style="width: 17%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Public</td>
<td>NO</td>
<td>bit</td>
<td>Если очередь публичная, она доступна для записи/чтения всем
Роботам</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания очереди</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>CreatedRobotName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Создавший очередь Робот</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>ChangedRobotAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время последнего изменения очереди Роботом</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>ChangedRobotName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Последний изменивший очередь Робот</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>TTL</td>
<td>YES</td>
<td>int</td>
<td>Время жизни элемента очереди (сек.)</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>MaxRetray</td>
<td>YES</td>
<td>int</td>
<td>Максимальное количество повторных помещений элемента в очередь при
фиксации статуса ошибка</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>RetrayType</td>
<td>YES</td>
<td>int</td>
<td>Тип повторного помещения элемента в очередь при ошибке. Error = 1,
BusinesError = 2</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>AnalyticsSchema</td>
<td>YES</td>
<td>nvarchar</td>
<td>JSON-схема, если задана, элемент должен соответствовать ей</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>OutputSchema</td>
<td>YES</td>
<td>nvarchar</td>
<td>JSON-схема, если задана, элемент должен соответствовать ей</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>SpecificSchema</td>
<td>YES</td>
<td>nvarchar</td>
<td>JSON-схема, если задана, элемент должен соответствовать ей</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>NaturalKeyUniqueness</td>
<td>YES</td>
<td>int</td>
<td>Тип уникальности натурального (пользовательского) ключа элемента
очереди обмена данными. Local = 0 (проверка на уникальность внутри
очереди), Global = 1</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>RobotCanDeleteOnlyItsOwnItem</td>
<td>NO</td>
<td>bit</td>
<td>Робот может удалять только свои (которые он создал) элементы
очереди</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>ValuesRobotLockTimeout</td>
<td>YES</td>
<td>int</td>
<td>Таймаут (сек), после которого снимается блокировка элементов
очереди</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>Encrypted</td>
<td>NO</td>
<td>bit</td>
<td>Все элементы очереди зашифрованы</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>PhysicalRemoval</td>
<td>NO</td>
<td>bit</td>
<td>Если True, то при удалении очередь и все ее элементы физически
удаляются из БД, иначе - логическое удаление.</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>ChangedAttendedUser</td>
<td>YES</td>
<td>nvarchar</td>
<td>Для аттендед-робота - последний изменивший очередь пользователь</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>FIFOLocked</td>
<td>YES</td>
<td>int</td>
<td>(устар.)</td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>FIFORetry</td>
<td>YES</td>
<td>int</td>
<td>Количество ретраев при извлечении по FIFO при FIFOLockedType.NoWait;
Если не задан, аналогичный параметр берется из конфига</td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>PrefetchBufferResetInterval</td>
<td>YES</td>
<td>int</td>
<td>Интервал (мсек) сброса PrefetchBuffer; Если не задан, аналогичный
параметр берется из конфига</td>
</tr>
<tr class="odd">
<td><ol start="25" type="1">
<li></li>
</ol></td>
<td>PrefetchDepth</td>
<td>YES</td>
<td>int</td>
<td>Глубина предварительной выборки для PrefetchBuffer.; Если не задан,
аналогичный параметр берется из конфига</td>
</tr>
<tr class="even">
<td><ol start="26" type="1">
<li></li>
</ol></td>
<td>PrefetchOffset</td>
<td>YES</td>
<td>int</td>
<td>Отступ предварительной выборки для PrefetchBuffer. Параметр
применяется случайным образом, если он больше 0.; Чтобы разные ноды
имели более высокий шанс заполнить свой PrefetchBuffer при его
одновременном заполнении; (для уменьшения вероятности попасть в
заблокированный жругой нодой элементы очереди); Если не задан,
аналогичный параметр берется из конфига</td>
</tr>
<tr class="odd">
<td><ol start="27" type="1">
<li></li>
</ol></td>
<td>SpeedModeInterval</td>
<td>YES</td>
<td>int</td>
<td>Интервал (мсек) между 2-мя последовательными запросами к чтению из
очереди по FIFO,; определяющий переключение в скоростной режим
(используется PrefetchBuffer); Если не задан, аналогичный параметр
берется из конфига</td>
</tr>
</tbody>
</table>

## ExchangeQueueStatisticAvgs

Среднее время обработки элемента очереди по окну. Ширина окна задается в
конфиге. Обновляется в фоновой службе через очередь в памяти

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 21%" />
<col style="width: 16%" />
<col style="width: 17%" />
<col style="width: 38%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AvgTime</td>
<td>YES</td>
<td>numeric</td>
<td>Среднее время обработки элемента очереди (мсек)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата/время создания окна</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления окна</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>WindowBottomAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Левая граница окна</td>
</tr>
</tbody>
</table>

## ExchangeQueueStatistics

Общая статистика очереди для обмена данными между Роботами. Обновляется
в фоновой службе через очередь в памяти

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 27%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>CountAll</td>
<td>NO</td>
<td>int</td>
<td>Всего элементов</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CountBusinessError</td>
<td>NO</td>
<td>int</td>
<td>Бизнес-ошибка</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CountEntryPrefetchBuffer</td>
<td>NO</td>
<td>int</td>
<td>Вход в PrefetchBuffer (возможно, только его формирование)</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>CountError</td>
<td>NO</td>
<td>int</td>
<td>Ошибка общего вида</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>CountInProgress</td>
<td>NO</td>
<td>int</td>
<td>Элемент прочитан (псевдостатус)</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>CountNew</td>
<td>NO</td>
<td>int</td>
<td>Элемент добавлен в очередь, еще не прочитан (псевдостатус)</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>CountPeekError</td>
<td>NO</td>
<td>int</td>
<td>Ошибка извлечения из очереди</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>CountPrefetchBufferError</td>
<td>NO</td>
<td>int</td>
<td>Ошибка формирования PrefetchBuffer</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>CountReadNoSpeedMode</td>
<td>NO</td>
<td>int</td>
<td>Чтение в обычном режиме</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>CountReadPrefetchBuffer</td>
<td>NO</td>
<td>int</td>
<td>Чтение из PrefetchBuffer</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>CountRemoved</td>
<td>YES</td>
<td>int</td>
<td>Кол-во элеиентов очереди, помеченных как удаленные (null для
очередей с физическим удалением элементов)</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>CountRetry</td>
<td>NO</td>
<td>int</td>
<td>Повтор</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>CountSuccess</td>
<td>NO</td>
<td>int</td>
<td>Успешно</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления</td>
</tr>
</tbody>
</table>

## ExchangeQueueValueEvents

Событие, связанное со значением из очереди. Элементы из очереди не
удаляются физически, они проходят некоторый воркфлоу, который
фиксируется как последовательность событий

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 25%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 38%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>bigint</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueValueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Элемент очереди (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Type</td>
<td>NO</td>
<td>int</td>
<td>Success = 0 (Завершилось успешно), Error = 1 (Завершилось с ошибкой.
Ошибка общего вида), BusinessError = 2 (Завершилось с
бизнес-ошибкой)</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Text</td>
<td>YES</td>
<td>nvarchar</td>
<td>Текст, который может сопровождать событие</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Опционально может также являться ключем секционирования</td>
</tr>
</tbody>
</table>

## ExchangeQueueValueMetadata

Дополнительные данные элемента очереди в виде словаря Ключ-Значение

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 25%" />
<col style="width: 14%" />
<col style="width: 17%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueValueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Элемент очереди (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Key</td>
<td>NO</td>
<td>nvarchar</td>
<td>Ключ</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>NO</td>
<td>nvarchar</td>
<td>Значение</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Опционально может также являться ключем секционирования</td>
</tr>
</tbody>
</table>

## ExchangeQueueValuePrefetchReadeds

Кэш в БД для предварительно извлеченного и прочитанного элемента, чтобы
при изменении его состояния, если PrefetchBuffer еще не синхронизирован
с БД, понимать, что элемент уже извлечен, и кем (Оркестраторный
Робот/Студия или Аттендед-робот) он извлечен. В отношении 1-1 с
ExchangeQueueValue. Таблица полностью очищается в
ExchangeQueuePrefetchBufferService при синхронизации PrefetchBuffer с БД

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Совпадает с Id из ExchangeQueueValue</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ReadedAttendedUser</td>
<td>YES</td>
<td>nvarchar</td>
<td>Для аттендед-робота - пользователь, который прочитал элемент
очереди</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>ReadedRobotId</td>
<td>YES</td>
<td>int</td>
<td>Робот, который взял (прочитал) в обработку элемент очереди; Только
один робот может взять элемент очереди в обработку</td>
</tr>
</tbody>
</table>

## ExchangeQueueValues

Элемент очереди

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 36%" />
<col style="width: 12%" />
<col style="width: 17%" />
<col style="width: 27%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Очередь (FR)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>NO</td>
<td>nvarchar</td>
<td>Значение (зашифрованное)</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>CreatedRobotId</td>
<td>YES</td>
<td>int</td>
<td>Создавший робот (FK)</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>DeadlineAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата, после которой элемент будут не доступен</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>LastEventId</td>
<td>YES</td>
<td>bigint</td>
<td>Последнее событие (FK)</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>PostponeAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата, до которой элемент не доступен</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ReadedRobotAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата прочтения элемента очереди роботом или студией. С позиции FIFO
этот элемент считается удаленным из очереди, но физически элемент не
удаляется</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>ReadedRobotId</td>
<td>YES</td>
<td>int</td>
<td>Прочитавший робот (FK)</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>Retray</td>
<td>NO</td>
<td>int</td>
<td>Количество повторных помещений элемента в очередь при фиксации
статуса ошибка</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>DeletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата удаления элемента очереди (не обязательно роботом)</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>Metadata</td>
<td>YES</td>
<td>nvarchar</td>
<td>Дополнительные данные в JSON (продублировано)</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>NaturalKey</td>
<td>YES</td>
<td>nvarchar</td>
<td>Натуральный (пользовательский) идентификатор (ключ) элемента
очереди. В зависимости от настроек очереди: может не проверяться на
уникальность, может проверяться на уникальность внутри очереди, может
проверяться на уникальность глобально</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueValuesRobotLockId</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Блокировка элемента</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>Encrypted</td>
<td>NO</td>
<td>bit</td>
<td>Элемент зашифрован и принадлежит зашифрованной очереди</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>Priority</td>
<td>YES</td>
<td>int</td>
<td>Приоритет - сначала сортировка по приоритетам, потом по дате - при
извлечении из очереди по FIFO или чтении с фильтром</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>RootId</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Корневой элемент, с которого началось повторение элементов в очереди
при ошибке. Для оптимизации построения цепочки повторенных элементов,
чтобы рекурсивно не строить по ParentId</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>CreatedAttendedUser</td>
<td>YES</td>
<td>nvarchar</td>
<td>Для аттендед-робота - пользователь, который создал элемент
очереди</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>DeletedReason</td>
<td>YES</td>
<td>int</td>
<td>Причина удаления</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>InProgressTimeout</td>
<td>YES</td>
<td>int</td>
<td>Таймаут (сек) по истечении которого элементы очереди; в статусе
InProgress считаются просроченными</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>PrefetchedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата предварительной выборки во временный буфер.; Используется в
высокоскоростном режиме чтения по FIFO</td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>PrefetchedNode</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, запросившей выборку во временный буфер</td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>ReadedAttendedUser</td>
<td>YES</td>
<td>nvarchar</td>
<td>Для аттендед-робота - пользователь, который прочитал элемент
очереди</td>
</tr>
</tbody>
</table>

## ExchangeQueueValueTags

Тэг элемента очереди. Тэг из справочника тегов

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 25%" />
<col style="width: 17%" />
<col style="width: 17%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueValueId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Элемент очереди (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TagId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Элемент справочника тегов (FK)</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
</tbody>
</table>

## ExchangeQueueValuesRobotLocks

Блокировка элементов очереди роботом. Заблокированному элементу ставится
ключ блокировки (Id). Другой робот не может обработать такой элемент -
изменить статус, удалить и т.п. Ключ блокировки формирует робот. По
этому ключу он разблокирует занятые элементы. Блокировка снимается по
таймауту (настройка очереди ValuesRobotLockTimeout) или через UI
Оркестратора

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 17%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>YES</td>
<td>int</td>
<td>Элемент справочника тегов (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>ExpiredAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата окончания блокировки по таймауту</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>AttendedUser</td>
<td>YES</td>
<td>nvarchar</td>
<td>Для аттендед-робота - пользователь, создавший блокировку</td>
</tr>
</tbody>
</table>

## FolderObjects[3]

Объект папки

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 30%" />
<col style="width: 23%" />
<col style="width: 23%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ObjectType</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>FolderId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>RpaProjectId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>WorkerId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>AgentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>AssetId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>DeployTemplateId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>RobotGroupId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>ScheduleId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>ProductionCalendarId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## FolderObjects2

Объект общей некорневой папки

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 30%" />
<col style="width: 23%" />
<col style="width: 23%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AgentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>AssetId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>DeployTemplateId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>FolderId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>ObjectType</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ProductionCalendarId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>RobotGroupId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>RpaProjectId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>ScheduleId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>WorkerId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## Folders[4]

Виртуальная папка в оркестраторе

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>ParentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Default</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
</tbody>
</table>

## Folders2

Виртуальная папка в оркестраторе (новая реализация, не Workspace, общая
папка). Такая папка является механизмом разделения прав пользователя на
объекты: RPA-проекты, роботы, задания и т.п. Может существовать отдельно
от пользователя. Корневая папка для тенанта физически не существует.
Считается, что объект принадлежит корневой папке, если он больше не
принадлежит никакой другой не корневой папке. Всем объектам, кроме
роботов и заданий, разрешено находиться в нескольких не корневых папках
одновременно

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 16%" />
<col style="width: 12%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>ParentId</td>
<td>YES</td>
<td>int</td>
<td>Родительская папка, для структуризации в виде дерева</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
</tbody>
</table>

## FolderUsers[5]

Пользователь папки

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 12%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>UserId</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>FolderId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Owner</td>
<td>NO</td>
<td>bit</td>
<td>Владелец папки</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Selected</td>
<td>NO</td>
<td>bit</td>
<td>Признак того, что папка сейчас выбрана пользователем для работы</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>FromUserId</td>
<td>YES</td>
<td>nvarchar</td>
<td>От какого пользователя предоставлен доступ к папке</td>
</tr>
</tbody>
</table>

## FolderUsers2

Пользователь общей папки. Права на Root-папку в таблице RootFolderUsers2

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 18%" />
<col style="width: 14%" />
<col style="width: 11%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>FromUserId</td>
<td>YES</td>
<td>nvarchar</td>
<td>От какого пользователя предоставлен доступ к папке</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>UserId</td>
<td>NO</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>FolderId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Owner</td>
<td>NO</td>
<td>bit</td>
<td>Владелец папки - пользователь, который её сам создал; У владельца
полные права на паку</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Selected</td>
<td>NO</td>
<td>bit</td>
<td>Признак того, что папка сейчас выбрана пользователем для работы;
Фильтрация к объектам будет применяться на основе этой папки</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>AccessType</td>
<td>YES</td>
<td>int</td>
<td>Тип переданных прав на папку - чтение, запись и т.д., если
пользователь не является её владельцем</td>
</tr>
</tbody>
</table>

## GeneralSettings

Системная таблица. Использовать нельзя

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 23%" />
<col style="width: 9%" />
<col style="width: 7%" />
<col style="width: 55%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>RpaProjectQueueProcessingType</td>
<td>NO</td>
<td>int</td>
<td>Параметры очереди проектов на выполнение</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TimeOffset</td>
<td>NO</td>
<td>int</td>
<td>Смещение времени в часах для дефолтного тенанта</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Email</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Password</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Pop3</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Pop3Port</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>RequireAuthenticate</td>
<td>YES</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>UseSsl</td>
<td>YES</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Login</td>
<td>YES</td>
<td>nvarchar</td>
<td>Если задано, используется вместо Email</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>RemoveReceived</td>
<td>YES</td>
<td>bit</td>
<td>Удалять письмо после получения</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>UseStandartNotSSLPort</td>
<td>YES</td>
<td>bit</td>
<td>Поставить true, если почтовик настроен на один из стандартных портов
(SMTP:25 or 587,POP3:110,IMAP:143); (не зависит от настройки UseSsl);
Подробнее:
https://github.com/jstedfast/MailKit/blob/master/FAQ.md#SslHandshakeException</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>ImapFolder</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>Imap</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>AgentTimeout</td>
<td>NO</td>
<td>int</td>
<td>Тайм-аут обращения к агенту</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>AgentPort</td>
<td>NO</td>
<td>int</td>
<td>Порт агента</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>AgentHttps</td>
<td>NO</td>
<td>bit</td>
<td>Использовать Https при обращении к агенту</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>DisabledDefaultTenant</td>
<td>NO</td>
<td>bit</td>
<td>Отключение дефолтного тенанта. Авторизация в нем будет не возможна.;
Пользовательский интерфейс для изменения этого поля не предусмотрен,
только через БД.</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>ImapPort</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## IncomingEmailLogs

Системная таблица

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 16%" />
<col style="width: 13%" />
<col style="width: 43%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>TriggerId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>MessageId</td>
<td>NO</td>
<td>nvarchar</td>
<td>Идентификатор письма на сервере</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Subject</td>
<td>NO</td>
<td>nvarchar</td>
<td>Тема письма</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>From</td>
<td>NO</td>
<td>nvarchar</td>
<td>Email отправителя письма</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Duplicate</td>
<td>NO</td>
<td>bit</td>
<td>Письмо забиралось с почтового сервера не однократно</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Triggered</td>
<td>NO</td>
<td>bit</td>
<td>Письмо вызвало срабатывание триггера</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## IncomingEmails

Настойки триггера с типом «Email»

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 24%" />
<col style="width: 12%" />
<col style="width: 11%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Email</td>
<td>NO</td>
<td>nvarchar</td>
<td>Email</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения записи</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Password</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Pop3</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Pop3Port</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>RequireAuthenticate</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>UseSsl</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>UseStandartNotSSLPort</td>
<td>NO</td>
<td>bit</td>
<td>Поставить true, если почтовик настроен на один из стандартных портов
(SMTP:25 or 587,POP3:110,IMAP:143); (не зависит от настройки
UseSsl)</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>ImapPort</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>ImapFolder</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>Imap</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>EWSUrl</td>
<td>YES</td>
<td>nvarchar</td>
<td>Адрес сервера ExchangeWebService, обязательно заполняется в формате
https://servername/EWS/Exchange.asmx,; например:
https://ms-exchange.s1.primo1.orch/EWS/Exchange.asmx. Перед добавлением
необходимо открыть ссылку в браузере; и убедиться что сервис
доступен.</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>RemoveReceived</td>
<td>NO</td>
<td>bit</td>
<td>Удалять письмо после получения</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>Login</td>
<td>YES</td>
<td>nvarchar</td>
<td>Если задано, используется вместо Email</td>
</tr>
</tbody>
</table>

## IncomingEmailWindowLogs

Системная таблица

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>TriggerId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>MinIndex</td>
<td>NO</td>
<td>int</td>
<td>Минимальный индекс письма</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>MaxIndex</td>
<td>NO</td>
<td>int</td>
<td>Максимальный индекс письма</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Size</td>
<td>NO</td>
<td>int</td>
<td>Размер окна - максимальное количество писем, забираемых за один
раз</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>IntevalInSeconds</td>
<td>NO</td>
<td>int</td>
<td>Интервал опроса почтового сервера</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Duplicates</td>
<td>NO</td>
<td>int</td>
<td>Количество дублей</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>Offset</td>
<td>NO</td>
<td>int</td>
<td>Смещение окна</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## IPv4Addresses

Упрощенное представление IpAddress (для ЧБ списка IP-шников для запуска
Primo.Studio)

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Address</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## IPv4Masks

Представление IP маски (для ЧБ списка IP-шников для запуска
Primo.Studio)

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Mask</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## LoadTests[6]

Нагрузочный тест

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 21%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>LoadTestScopeId</td>
<td>NO</td>
<td>int</td>
<td>Сценарий нагрузочного тестирования</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>RpaProjectId</td>
<td>NO</td>
<td>int</td>
<td>Rpa-проект с нагрузочным тестированием</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>LoadTestScheduleId</td>
<td>NO</td>
<td>int</td>
<td>Расписание нагрузочного тестирования</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ParentId</td>
<td>YES</td>
<td>int</td>
<td>Родительский тест</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>FiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания триггера шедулера</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>LockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Блокировка (служебное поле) , чтобы одновременно несколько инстансов
не поставили в очередь выполнения Rpa-проект этого теста</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>NodeLock</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, заблокировавшей тест в БД</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>NO</td>
<td>int</td>
<td>Служебное поле для разруливания конкурентного доступа</td>
</tr>
</tbody>
</table>

## LoadTestScheduleItemActiveRobots[7]

Робот активности элемента расписания нагрузочного теста при выполнении
теста

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 31%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>LoadTestScheduleItemActiveId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>DeltaThreads</td>
<td>YES</td>
<td>int</td>
<td>Изменение количества потоков</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата добавления робота</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>DeletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>При снижении количества потоков (освобождении роботов) сразу их не
удаляем, оставляем для мониторинга</td>
</tr>
</tbody>
</table>

## LoadTestScheduleItemActives[8]

Активность элемента расписания нагрузочного теста при выполнении теста

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 30%" />
<col style="width: 21%" />
<col style="width: 16%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>LoadTestScheduleItemId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>LoadTestId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>FiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания</td>
</tr>
</tbody>
</table>

## LoadTestScheduleItems[9]

Элемент расписания нагрузочного теста

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 23%" />
<col style="width: 19%" />
<col style="width: 14%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>LoadTestScheduleId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Duration</td>
<td>NO</td>
<td>time</td>
<td>Продолжительность</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>DeltaThreads</td>
<td>NO</td>
<td>int</td>
<td>Изменение количества потоков</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>IterationInterval</td>
<td>NO</td>
<td>int</td>
<td>Интервал между итерациями</td>
</tr>
</tbody>
</table>

## LoadTestSchedules[10]

Расписание нагрузочного теста

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 21%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>RobotConstThreads</td>
<td>YES</td>
<td>int</td>
<td>Одинаковое для всех роботов количество потоков</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>RobotSoftKill</td>
<td>NO</td>
<td>bit</td>
<td>Использовать мягкое завершение роботов</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>DefaultKX</td>
<td>YES</td>
<td>int</td>
<td>Коэффициент трансформации по умолчанию графика расписания по X (от 1
до 100)</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>DefaultKY</td>
<td>YES</td>
<td>int</td>
<td>Коэффициент трансформации по умолчанию графика расписания по Y (от 1
до 100)</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
</tbody>
</table>

## LoadTestScopes[11]

Сценарий нагрузочного тестирования - контейнер нескольких нагрузочных
тестов

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 47%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Signal</td>
<td>YES</td>
<td>int</td>
<td>Управляющий сигнал на изменение состояния сценария нагрузочного
тестирования</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>SignalCreatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время создания управляющего сигнала на изменение состояния
сценария нагрузочного тестирования</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>StartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время запуска</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Status</td>
<td>NO</td>
<td>int</td>
<td>Состояние</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>StateChangedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время изменения состояния</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>WithTriggers</td>
<td>NO</td>
<td>bit</td>
<td><p>True - запуск по триггеру</p>
<p>False - ручной запуск</p></td>
</tr>
</tbody>
</table>

## LoadTestScopeSchedulerSignalNodeConfirms[12]

Подтверждение получения сигнала для шедулеров сценариев нагрузочного
тестирования у ноды

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 23%" />
<col style="width: 18%" />
<col style="width: 17%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор ноды WebApi</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Confirm</td>
<td>NO</td>
<td>bit</td>
<td>Подтверждение</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления записи</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>LoadTestScopeId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## LoadTestScopeTriggers[13]

Триггер для сценария нагрузочного тестирования

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 32%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Type</td>
<td>NO</td>
<td>int</td>
<td>Тип триггера</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания триггера</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения триггера</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>LoadTestScopeId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>FiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания триггера</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>FiredAtEmail</td>
<td>YES</td>
<td>datetime2</td>
<td>Только для триггера TriggerType.Email - дата получения новых
писем</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>LastErrorMsg</td>
<td>YES</td>
<td>nvarchar</td>
<td>Сообщение об ошибке при последнем срабатывании</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ScheduleId</td>
<td>YES</td>
<td>int</td>
<td>Расписание</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>NextFiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата следующего запуска триггера шедулера</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>IncomingEmailId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>IncomingFrom</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>IncomingSubject</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>IncomingEmailWindowSize</td>
<td>YES</td>
<td>int</td>
<td>Максимальное количество писем, забираемых за один раз</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>IncomingEmailIntevalInSeconds</td>
<td>YES</td>
<td>int</td>
<td>Интервал запросов к почтовому серверу</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>ByLoadTestScopeId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>LockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Блокировка (служебное поле), чтобы одновременно несколько инстансов
не поставили в очередь выполнение проекта задания этого триггера</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>NodeLock</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, заблокировавшей триггер в БД</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>NO</td>
<td>int</td>
<td>Служебное поле для разруливания конкурентного доступа</td>
</tr>
</tbody>
</table>

## LogsDump

Системная таблица

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>StartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CompletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TotalFilesCount</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>CompletedCount</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## Nodes

Информация о ноде кластера WebApi. Пишется самой нодой

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 18%" />
<col style="width: 13%" />
<col style="width: 12%" />
<col style="width: 49%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи о ноде</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>UdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения записи о ноде. Если запись не обновляется в течение
таймаута,; остальные ноды считают эту ноду выведенной из кластера</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>NodeId</td>
<td>NO</td>
<td>int</td>
<td>Идентификатор ноды. Берется из конфигурационного файла ноды
WebApi</td>
</tr>
</tbody>
</table>

## NuGetTasks

Задача для NuGet-сервера

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>PackageFileName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Имя файла пакета, TestLib.5.0.0.nupkg, который требуется
опубликовать</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания задачи</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>StartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата старта задачи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>FileSize</td>
<td>NO</td>
<td>bigint</td>
<td>Фактически записанный на диск размер файла</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>ContentLength</td>
<td>NO</td>
<td>bigint</td>
<td>ContentLength передаваемый в заголовке http на upload файла.;
Совместно с FileSize используется для определения процента загрузки</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>UploadedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время загрузки версии дистрибутива.; Проставляется после
полного скачивания файла на диск</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>CompletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата выполнения задачи; Выполненные задачи через некоторое время
удаляются</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>CompletedSuccess</td>
<td>YES</td>
<td>bit</td>
<td>Результат вата выполнения задачи</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Type</td>
<td>NO</td>
<td>int</td>
<td>Тип задачи</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>PackageId</td>
<td>YES</td>
<td>nvarchar</td>
<td>ID пакета, который требуется удалить</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>PackageVersion</td>
<td>YES</td>
<td>nvarchar</td>
<td>Версия пакета, который требуется удалить</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>ErrorMsg</td>
<td>YES</td>
<td>nvarchar</td>
<td>Последняя ошибка при выполнении задачи</td>
</tr>
</tbody>
</table>

## ProductionCalendars

Производственный календарь

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 47%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Year</td>
<td>YES</td>
<td>int</td>
<td>Год</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Date</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Type</td>
<td>NO</td>
<td>int</td>
<td>Working = 0 (рабочий), NoWorking = 1 (не рабочий), PreHoliday = 2
(предпраздничный)</td>
</tr>
</tbody>
</table>

## ProductionCalendar2

Производственный календарь шапка (множественные календари на один год)

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 26%" />
<col style="width: 20%" />
<col style="width: 16%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Year</td>
<td>NO</td>
<td>int</td>
<td>Год</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>NO</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Priority</td>
<td>NO</td>
<td>int</td>
<td>Приоритет</td>
</tr>
</tbody>
</table>

## ProductionCalendar2Items

Производственный календарь дни (множественные календари на один год)

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 26%" />
<col style="width: 20%" />
<col style="width: 16%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ProductionCalendarId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Date</td>
<td>NO</td>
<td>datetime2</td>
<td>День года</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Type</td>
<td>NO</td>
<td>int</td>
<td>Тип дня</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>Yes</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
</tbody>
</table>

## Rdp2AddressFilters

Производственный календарь дни (множественные календари на один год)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Item</td>
<td>NO</td>
<td>nvarchar</td>
<td>Элемент AddressFilter - IP или имя машины. Натуральный ключ</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Host</td>
<td>NO</td>
<td>nvarchar</td>
<td>IP сервера с RDP2, на котором настроен AddressFilter</td>
</tr>
</tbody>
</table>

## RobotAgentSessions

Системная (Робот, удерживающий RDP-сессию)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 46%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AgentId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>ReleasedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата освобождения роботом RDP-сессии</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>ProjectId</td>
<td>NO</td>
<td>int</td>
<td>У проекта могут быть параметры, влияющие на открытие/закрытие
сессии</td>
</tr>
</tbody>
</table>

## RobotDeployTrackings

Системная (Трекинг деплоя Робота)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 15%" />
<col style="width: 13%" />
<col style="width: 45%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата вставки записи</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td>Робот</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Stage</td>
<td>NO</td>
<td>int</td>
<td>Стадия деплоя</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Success</td>
<td>NO</td>
<td>bit</td>
<td>Результат (успешно/не успешно)</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>ErrorMsg</td>
<td>YES</td>
<td>nvarchar</td>
<td>Текст сообщения об ошибке</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Port</td>
<td>YES</td>
<td>int</td>
<td>Актуальный порт Робота, который зарезервирован для него при
деплое</td>
</tr>
</tbody>
</table>

## RobotDistrExistsNodeConfirms

Системная (Подтверждение наличия дистрибутива Робота в папке
дистрибутива)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 21%" />
<col style="width: 16%" />
<col style="width: 17%" />
<col style="width: 39%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор ноды WebApi</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Exists</td>
<td>NO</td>
<td>bit</td>
<td>Дистрибутив существует в папке</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления записи</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>RobotDistrId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>ExistsUpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления записи для Exists = true</td>
</tr>
</tbody>
</table>

## RobotDistrs

Системная (Дистрибутив Робота)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 28%" />
<col style="width: 12%" />
<col style="width: 17%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>FileSize</td>
<td>NO</td>
<td>bigint</td>
<td>Фактически записанный на диск размер файла</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>ContentLength</td>
<td>NO</td>
<td>bigint</td>
<td>ContentLength передаваемый в заголовке http на upload файла.
Совместно с FileSize используется для определения процента загрузки</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>UploadedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время загрузки версии дистрибутива.Проставляется после полного
скачивания файла на диск</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>YES</td>
<td>nvarchar</td>
<td>Версия дистрибутива</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Activated</td>
<td>YES</td>
<td>bit</td>
<td>Активирован</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>ActivatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время активации</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>X64</td>
<td>YES</td>
<td>bit</td>
<td>Платформа (x64, x86)</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание. Основное назначение - не путать дистрибутивы одинаковой
версии</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Linux</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>NodesDesynchronizationAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Долгое время от какой-либо ноды нет подтверждения</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>NodeSequentialSwitchingAt</td>
<td>YES</td>
<td>datetime2</td>
<td>В серии последовательных согласований (задается в конфиге)
подтверждение постоянно меняется</td>
</tr>
</tbody>
</table>

## RobotGroupItems

Привязка робота к группе

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 30%" />
<col style="width: 24%" />
<col style="width: 18%" />
<col style="width: 18%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>GroupId</td>
<td>NO</td>
<td>int</td>
<td>Группа (FK)</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td>Робот (FK)</td>
</tr>
</tbody>
</table>

## RobotGroups

Группа робота

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 26%" />
<col style="width: 20%" />
<col style="width: 16%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>PK</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
</tbody>
</table>

## Robots

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 35%" />
<col style="width: 12%" />
<col style="width: 17%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>WorkerId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Key</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Port</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>RobotUserName</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>RobotPassword</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Deployment</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>CurrentPlatform</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>CurrentTemplateId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>Lang</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>CurrentProjectId</td>
<td>YES</td>
<td>int</td>
<td>Текущий проект робота</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>CurrentProjectAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата назначения текущего проекта Оркестратором</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>CurrentProjectStartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата запуска текущего проекта Роботом</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>Status</td>
<td>NO</td>
<td>int</td>
<td>Статус Робота</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>StatusDate</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>Disabled</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>YES</td>
<td>nvarchar</td>
<td>Версия дистрибутива</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>Edition</td>
<td>NO</td>
<td>int</td>
<td>Редакция</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>CurrentProjectCompletedNoErrors</td>
<td>YES</td>
<td>bit</td>
<td>Выполнение текущего проекта завершено Роботом без ошибок</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>CurrentProjectCompletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>LockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Признак блокировки Оркестратором (не "приложения на машине Робота",
а "сущности в БД Оркестратора")</td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>SoftKillSendAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата, когда Оркестратор попросил Робота убиться</td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>LastStartOperationKey</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Идентификатор последней операции старта</td>
</tr>
<tr class="odd">
<td><ol start="25" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="26" type="1">
<li></li>
</ol></td>
<td>CurrentAssignmentId</td>
<td>YES</td>
<td>int</td>
<td>Задание, в рамках которого назначен роботу проект на выполнение</td>
</tr>
<tr class="odd">
<td><ol start="27" type="1">
<li></li>
</ol></td>
<td>DeploymentError</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="28" type="1">
<li></li>
</ol></td>
<td>AgentLockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Признак блокировки Робота Агентом</td>
</tr>
<tr class="odd">
<td><ol start="29" type="1">
<li></li>
</ol></td>
<td>AgentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="30" type="1">
<li></li>
</ol></td>
<td>PushStatus</td>
<td>NO</td>
<td>bit</td>
<td><p>Если false, Оркестратор получает Status Робота через его
опрос</p>
<p>Если true, Агент собирает Status Роботов и пачкой отправляет в
Оркестратор</p></td>
</tr>
<tr class="odd">
<td><ol start="31" type="1">
<li></li>
</ol></td>
<td>StartError</td>
<td>NO</td>
<td>int</td>
<td>Тип ошибки при старте робота</td>
</tr>
<tr class="even">
<td><ol start="32" type="1">
<li></li>
</ol></td>
<td>HardKillStartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата старта команды принудительного останова робота</td>
</tr>
<tr class="odd">
<td><ol start="33" type="1">
<li></li>
</ol></td>
<td>EngineVersion</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="34" type="1">
<li></li>
</ol></td>
<td>AliveInterval</td>
<td>YES</td>
<td>int</td>
<td>Интервал (мсек), черезкоторый робот шлет свое состояние; Если не
задан, используется из конфигурационного файла</td>
</tr>
<tr class="odd">
<td><ol start="35" type="1">
<li></li>
</ol></td>
<td>Linux</td>
<td>YES</td>
<td>bit</td>
<td>Дистрибутив для Linux; Версия дистрибутива при этом может быть таже,
что и для Windows</td>
</tr>
<tr class="even">
<td><ol start="36" type="1">
<li></li>
</ol></td>
<td>NodeId</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, которая меняла запись</td>
</tr>
<tr class="odd">
<td><ol start="37" type="1">
<li></li>
</ol></td>
<td>AdAuth</td>
<td>NO</td>
<td>bit</td>
<td>Используется AD-аутентификация (RDP-учетка или учетка машины
робота)</td>
</tr>
<tr class="even">
<td><ol start="38" type="1">
<li></li>
</ol></td>
<td>UserName</td>
<td>YES</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="39" type="1">
<li></li>
</ol></td>
<td>UserPassword</td>
<td>YES</td>
<td>nvarchar</td>
<td>Пароль пользователя оркестратора. Должен совпадать с паролем из
Users (там он не хранится)</td>
</tr>
</tbody>
</table>

## RobotSoftKillSignals

Сигнал мягкого останова для робота (1-1 с таблицей Robots)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 14%" />
<col style="width: 17%" />
<col style="width: 43%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td>Совпадает с Id из Robots, связь 1-1</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>OperationKey</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotKey</td>
<td>YES</td>
<td>nvarchar</td>
<td>Натуральный PK. Используется при опросе таблицы роботами, чтобы не
делать запрос в таблицу Robots</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedtAt</td>
<td>NO</td>
<td>datetime2</td>
<td>-</td>
</tr>
</tbody>
</table>

## RobotStartTrackings

Трекинг старта Робота

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 18%" />
<col style="width: 14%" />
<col style="width: 39%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата вставки записи</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения записи</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td>Робот</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Stage</td>
<td>NO</td>
<td>int</td>
<td>Стадия старта</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Success</td>
<td>NO</td>
<td>bit</td>
<td>Результат (успешно/не успешно)</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>ErrorMsg</td>
<td>YES</td>
<td>nvarchar</td>
<td>Текст сообщения об ошибке</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>NumberRequest</td>
<td>YES</td>
<td>int</td>
<td>Номер попытки обращения к роботу</td>
</tr>
</tbody>
</table>

## RobotUnlockQueue

Очередь разблокировки робота. Отправляется сюда, если по какой-то
причине не получилось разблокировать робота, например, не доступна
машина робота

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Ip</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>RobotKey</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>UpdateCount</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## RolePermissions

Права

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 17%" />
<col style="width: 13%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>RoleId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор роли из БД ltoolsidentity</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>JsonValue</td>
<td>YES</td>
<td>nvarchar</td>
<td>Сериализованное значение прав</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
</tbody>
</table>

## RootFolderUsers2

Права на Root-папку

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 19%" />
<col style="width: 14%" />
<col style="width: 11%" />
<col style="width: 48%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>UserId</td>
<td>NO</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>AccessType</td>
<td>YES</td>
<td>int</td>
<td>Тип прав на папку - чтение, запись и т.д.; Вариантом сбросить права
является установить в null</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>FromUserId</td>
<td>NO</td>
<td>nvarchar</td>
<td>-</td>
</tr>
</tbody>
</table>

## RpaProjectArchiveExistsNodeConfirms

Подтверждение наличия архива RPA-проекта в папке RPA-проектов

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 18%" />
<col style="width: 17%" />
<col style="width: 35%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Node</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор ноды WebApi</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Exists</td>
<td>NO</td>
<td>bit</td>
<td>Дистрибутив существует в папке</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время обновления записи</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>RpaProjectArchiveId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
</tbody>
</table>

## RpaProjectArchives

RPA-проект

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 42%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Body</td>
<td>YES</td>
<td>varbinary</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>ProjectId</td>
<td>YES</td>
<td>int</td>
<td>При создании сначала на диск сохраняется файл архива, и только потом
ему назначается ProjectId</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>ContentLength</td>
<td>NO</td>
<td>bigint</td>
<td>ContentLength передаваемый в заголовке http на upload файла</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>FileId</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>FileSize</td>
<td>NO</td>
<td>bigint</td>
<td>Фактически записанный на диск размер файла</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>UploadedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время загрузки файла</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>ProjectName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Название проекта (извлекаем из файла проекта). Основное назначение -
автоматически заполнить поле Название проекта</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>ProjectVersion</td>
<td>YES</td>
<td>nvarchar</td>
<td>Номер версии (в соответствии с принятой системой нумерации версий у
разработчиков проектов).</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>PreRelease</td>
<td>NO</td>
<td>bit</td>
<td>Признак, что версия является предрелизной.</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>VersionComments</td>
<td>YES</td>
<td>nvarchar</td>
<td>Комментарий к текущей версии проекта (сырые данные, считываемые из
архива с проектом при его загрузке в орк)</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>TagsAsString</td>
<td>YES</td>
<td>nvarchar</td>
<td>Тэги (строка с разделителями ;) для текущей версии проекта (сырые
данные, считываемые из архива с проектом при его загрузке в орк)</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>IdeaHubId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор шаблона проекта из IdeaHub (сырые данные, считываемые
из архива с проектом при его загрузке в орк)</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>ParsedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время окончания обработки файла.</td>
</tr>
</tbody>
</table>

## RpaProjectLaunches

Запуск Rpa-проекта

<table style="width:100%;">
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 12%" />
<col style="width: 17%" />
<col style="width: 41%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>OperationKey</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Натуральный ключ</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>ProjectId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>StartedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата запуска</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>CompletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата завершения</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Success</td>
<td>YES</td>
<td>bit</td>
<td>Результат</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>KilledAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата принудительного завершения через Оркестратор</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>TriggerId</td>
<td>YES</td>
<td>int</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>RobotStartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата получение сигнала старта от робота</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>LaunchChainKey</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Ключ цепочки запусков. Не используется для ручного запуска робота с
проектом</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>Manual</td>
<td>YES</td>
<td>bit</td>
<td>Ручной запуск робота с проектом. Чтобы отличать от ручного помещения
проекта в очередь проектов; Строго для AssignmentId = null</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>TimeoutAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Освобождение робота по таймауту</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>RdpSessionStartedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата открытия RDP-сессии; Если загрузка профиля пользователя длится
долго (дольше периода итерации в StartRobotCommandBusService),; то
сначала установится эта дата. Иначе она будет пустая (тогда пользоваться
UserProfileLoadedAt); Также эта дата установится, если ожидание загрузки
профиля пользователя отключено в конфиге</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>UserProfileLoadedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата загрузки профиля пользователя. Профиль пользователя загружается
обязательно после; открытия RDP-сессии; Не устанавливается, если
ожидание загрузки профиля пользователя отключено в конфиге</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>ErrorAt</td>
<td>YES</td>
<td>datetime2</td>
<td>-</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>ErrorType</td>
<td>YES</td>
<td>int</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>Repeated</td>
<td>YES</td>
<td>bit</td>
<td>Был ли запуск повторен из UI орка (ручной запуск, но при этом
AssignmentId может быть не null)</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>NodeId</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор узла, занявшего записи</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>RdpSessionBeginAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата начала открытия RDP-сессии. Чтобы по завершении можно было
оценить затраченное на открытие; RDP-сессии/ожидание загрузки профиля
пользователя время</td>
</tr>
</tbody>
</table>

## RpaProjectLaunchVariables

Переменная Rpa-проекта, которую робот считает/запишет по OperationKey

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 18%" />
<col style="width: 14%" />
<col style="width: 38%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>RpaProjectLaunchId</td>
<td>NO</td>
<td>int</td>
<td>Запуск Rpa-проекта</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RpaProjectVariableId</td>
<td>NO</td>
<td>int</td>
<td>Переменная проекта</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td>Строковое представление значения</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>ReadedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>WrittedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
</tbody>
</table>

## RpaProjectQueue

Состояние очереди проектов на выполнение - только для отображения в UI,
в качестве реальной очереди используется RabbitMQ

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 24%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 38%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ProjectId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Lost</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>PublishFailed</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>OperationKey</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Идентификатор операции</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>YES</td>
<td>int</td>
<td>Робот, которому на выполнение назначен проект</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>InstanceCreatedId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>InstanceUpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>InstanceUpdatedId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>ErrorMsg</td>
<td>YES</td>
<td>nvarchar</td>
<td>Текст ошибки запуска</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>ErrorRobotId</td>
<td>YES</td>
<td>int</td>
<td>Робот, на котором произошел сбой запуска</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>ForceDeletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Признак ручного (принудительного) удаления проекта из очереди</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>YES</td>
<td>int</td>
<td>Задание, в рамках которого проект назначается на выполнение</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>DurationLevel</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>TriggerEventJson</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>ReadedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата извлечения из очереди без подтверждения</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>Repeated</td>
<td>YES</td>
<td>bit</td>
<td>Повторный запуск из UI Оркестратора</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>WorkerOverflowCount</td>
<td>NO</td>
<td>int</td>
<td>Количество повторных помещений в очередь по причине перегруженности
машины робота</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>LaunchChainKey</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td>Ключ цепочки запусков.</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>UserFolderId</td>
<td>NO</td>
<td>int</td>
<td>Папка пользователя, в контексте которой произощло событие; Для
кэширования списка Id роботов папки</td>
</tr>
</tbody>
</table>

## RpaProjectRobots 

Привязка роботов к проекту

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 21%" />
<col style="width: 17%" />
<col style="width: 13%" />
<col style="width: 41%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ProjectId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>RobotId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Ord</td>
<td>NO</td>
<td>int</td>
<td>Чем выше, тем приоритетней</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Reason</td>
<td>YES</td>
<td>nvarchar</td>
<td>Причина, по которой осуществлена привязка</td>
</tr>
</tbody>
</table>

## RpaProjectTags

Тэг RPA-проекта

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 29%" />
<col style="width: 23%" />
<col style="width: 23%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>RpaProjectId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TagId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td></td>
</tr>
</tbody>
</table>

## RpaProjectWorkflows

Процесс Rpa-проекта, прочитанный из файла

<table>
<colgroup>
<col style="width: 7%" />
<col style="width: 29%" />
<col style="width: 23%" />
<col style="width: 23%" />
<col style="width: 15%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>FileId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Workflow</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## RpaProjects 

RpaProject-файл и его параметры запуска

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 32%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Глобально уникальное наименование проекта</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание проекта</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>MainWorkflow</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>SoftPlatform</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Disabled</td>
<td>NO</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>RunConfig</td>
<td>YES</td>
<td>int</td>
<td>Конфигурация запуска стандартная</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>RunConfigCustom</td>
<td>YES</td>
<td>nvarchar</td>
<td>Конфигурация запуска специальная</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>Mock</td>
<td>NO</td>
<td>bit</td>
<td>Использовать заглушки</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>DurationLevel</td>
<td>YES</td>
<td>int</td>
<td>Уровень продолжительности задержки в очереди задержки</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>ParentId</td>
<td>YES</td>
<td>int</td>
<td>Родительская версия</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>NO</td>
<td>int</td>
<td>Номер версии</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>RobotDistrVersions</td>
<td>YES</td>
<td>nvarchar</td>
<td>Список версий дистрибутивов роботов</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>CloseRDPSession</td>
<td>NO</td>
<td>bit</td>
<td>После выполнения проекта роботом закрыть RDP-сессию</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>Active</td>
<td>NO</td>
<td>bit</td>
<td>Флаг активности</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>ProjectArchiveId</td>
<td>YES</td>
<td>int</td>
<td>Заполняется после загрузки файла проекта, дублирует 1-1 связь в
существующей реализации</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>ExclusiveLaunch</td>
<td>NO</td>
<td>bit</td>
<td>Проект запускается в единственном экземпляре</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>NoDuplicateDeferredQueue</td>
<td>NO</td>
<td>bit</td>
<td>Не повторять в очереди ожидания</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>PublishSource</td>
<td>YES</td>
<td>int</td>
<td>Источник, из которого был опубликован проект (залит архив)</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>ProjectVersion</td>
<td>YES</td>
<td>nvarchar</td>
<td>Номер версии (в соответствии с принятой системой нумерации версий у
разработчиков проектов).; Берется из метаданных проекта. Может быть
отредактировано</td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>PreRelease</td>
<td>NO</td>
<td>bit</td>
<td>Признак, что версия является предрелизной.; Берется из метаданных
проекта или устанавливается Оркестратором.</td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>VersionComments</td>
<td>YES</td>
<td>nvarchar</td>
<td>Комментарии к текущей версии</td>
</tr>
<tr class="odd">
<td><ol start="25" type="1">
<li></li>
</ol></td>
<td>IdeaHubId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Глобально-уникальный идентификатор шаблона проекта, определяемый в
IdeaHub</td>
</tr>
<tr class="even">
<td><ol start="26" type="1">
<li></li>
</ol></td>
<td>LimitedLaunch</td>
<td>YES</td>
<td>int</td>
<td>Ограниченный запуск</td>
</tr>
<tr class="odd">
<td><ol start="27" type="1">
<li></li>
</ol></td>
<td>SessionsReleaseDelay</td>
<td>NO</td>
<td>int</td>
<td>Задержка релиза сессии (мсек) - сессия может очень быстро
понадобиться; другому роботу, чтобы её не пересоздавать заново. Только
для ExclusiveSessionsRelease = false</td>
</tr>
<tr class="even">
<td><ol start="28" type="1">
<li></li>
</ol></td>
<td>ExclusiveSessionsRelease</td>
<td>NO</td>
<td>bit</td>
<td>Если поднят этот флаг, робот, когда освобождает сессию, не смотрит
на отсутствие релиза сессии у других роботов.; Должно использоваться,
когда только один робот закрывает сессию,; чтобы не ломать работу
остальных роботов в этой сессии</td>
</tr>
<tr class="odd">
<td><ol start="29" type="1">
<li></li>
</ol></td>
<td>IgnoreProjectCompletedTrigger</td>
<td>NO</td>
<td>bit</td>
<td>Завершение процесса может триггерить запуск задания; Если false, то
завершение процесса не зажигает триггер</td>
</tr>
</tbody>
</table>

## RpaProjectVariables

Привязка переменных проекта к заданию. Эти переменные считываются при
загрузке проекта. Их список и имена (и значение, если есть) –
фиксированы, через UI Оркестратора и роботами не меняется

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 20%" />
<col style="width: 16%" />
<col style="width: 12%" />
<col style="width: 44%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>ProjectId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование переменной. Уникальное в рамках проекта</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td>Строковое представление значения</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Direction</td>
<td>NO</td>
<td>Int</td>
<td>Направление</td>
</tr>
</tbody>
</table>

## RpaProjectVariableTemps

Переменная Rpa-проекта, прочитанная из файла проекта и временно
сохраненная для привязки к проекту

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 22%" />
<col style="width: 17%" />
<col style="width: 17%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>FileId</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>MainWorkflow</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>YES</td>
<td>nvarchar</td>
<td>Строковое представление значения</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Direction</td>
<td>NO</td>
<td>Int</td>
<td>Направление</td>
</tr>
</tbody>
</table>

## Schedules

Расписание

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 24%" />
<col style="width: 14%" />
<col style="width: 12%" />
<col style="width: 41%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Description</td>
<td>YES</td>
<td>nvarchar</td>
<td>Описание</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CronString</td>
<td>YES</td>
<td>nvarchar</td>
<td>Крон-строка расписания</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>ScheduleJson</td>
<td>YES</td>
<td>nvarchar</td>
<td>Сериализованная в Json ViewModel формы настройки расписания</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>IgnoredSaSu</td>
<td>NO</td>
<td>bit</td>
<td>Суббота и воскресенье - рабочие дни</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>UseProductionCalendar</td>
<td>NO</td>
<td>bit</td>
<td>Согласовано с производственным календарем</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>ScheduleModifiedDate</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата последнего редактирования расписания</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>ProductionCalendarId</td>
<td>YES</td>
<td>int</td>
<td>Согласовано с производственным календарем</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>ProductionCalendar2Id</td>
<td>YES</td>
<td>int</td>
<td>Согласовано с производственным календарем2</td>
</tr>
</tbody>
</table>

## StatesSlaConfig

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 42%" />
<col style="width: 12%" />
<col style="width: 10%" />
<col style="width: 28%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>AgentUnavailabilityFirstSec</td>
<td>NO</td>
<td>int</td>
<td>Продолжительность недоступности Агента после которой считается, что
он не доступен</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>AgentUnavailabilityRepeatedlySec</td>
<td>NO</td>
<td>int</td>
<td>Продолжительность недоступности Агента после которой происходит
повторное оповещение</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>RpaProjectQueueRiseCriticalQueueLength</td>
<td>NO</td>
<td>int</td>
<td>Критическая длина очереди</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>RpaProjectQueueRiseRepeatedlySec</td>
<td>NO</td>
<td>int</td>
<td>Продолжительность нахождения очереди в критическом состоянии после
которой происходит повторное оповещение</td>
</tr>
</tbody>
</table>

## Tags

Тэг. Используется для поиска объектов

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 27%" />
<col style="width: 22%" />
<col style="width: 21%" />
<col style="width: 20%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Value</td>
<td>NO</td>
<td>nvarchar</td>
<td>Значение</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания</td>
</tr>
</tbody>
</table>

## Tenants

Тенант (для случая, когда тенанты хранятся в БД)

<table>
<colgroup>
<col style="width: 4%" />
<col style="width: 22%" />
<col style="width: 9%" />
<col style="width: 8%" />
<col style="width: 54%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>NO</td>
<td>nvarchar</td>
<td>Наименование тенанта</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>TimeOffset</td>
<td>NO</td>
<td>int</td>
<td>Смещение времени в часах</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения записи</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>DeletedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата удаления записи</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>Email</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>Password</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>Pop3</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Pop3Port</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>RequireAuthenticate</td>
<td>YES</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>UseSsl</td>
<td>YES</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>AgentHttps</td>
<td>NO</td>
<td>bit</td>
<td>Использовать Https при обращении к агенту</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>UseStandartNotSSLPort</td>
<td>YES</td>
<td>bit</td>
<td>Поставить true, если почтовик настроен на один из стандартных портов
(SMTP:25 or 587,POP3:110,IMAP:143); (не зависит от настройки UseSsl);
Подробнее:
https://github.com/jstedfast/MailKit/blob/master/FAQ.md#SslHandshakeException</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>Login</td>
<td>YES</td>
<td>nvarchar</td>
<td>Если задано, используется вместо Email</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>RemoveReceived</td>
<td>YES</td>
<td>bit</td>
<td>Удалять письмо после получения</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>RpaProjectQueueProcessingType</td>
<td>YES</td>
<td>int</td>
<td>Параметры очереди проектов на выполнение; Если не задан,
используется из GeneralSettings</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>ImapPort</td>
<td>YES</td>
<td>int</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>ImapFolder</td>
<td>YES</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>Imap</td>
<td>YES</td>
<td>nvarchar</td>
<td>-</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>AgentPort</td>
<td>NO</td>
<td>int</td>
<td>Порт агента</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>AgentTimeout</td>
<td>NO</td>
<td>int</td>
<td>Тайм-аут обращения к агенту</td>
</tr>
</tbody>
</table>

## Triggers

Триггер для задания

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 33%" />
<col style="width: 13%" />
<col style="width: 17%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Type</td>
<td>NO</td>
<td>int</td>
<td>Тип триггера</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания триггера</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>UpdatedAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата изменения триггера</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>AssignmentId</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>FiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания триггера</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>LastErrorMsg</td>
<td>YES</td>
<td>nvarchar</td>
<td>Сообщение об ошибке при последнем срабатывании</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>ScheduleId</td>
<td>YES</td>
<td>int</td>
<td>Расписание</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>NextFiredAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата следующего запуска триггера шедулера</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>IncomingEmailId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>ExchangeQueueId</td>
<td>YES</td>
<td>uniqueidentifier</td>
<td>Очередь обмена данными</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>WorkerId</td>
<td>YES</td>
<td>int</td>
<td>Машина Робота</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>WorkerFolder</td>
<td>YES</td>
<td>nvarchar</td>
<td>Папка на машине Робота</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>RpaProjectId</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>ProjectCompletedOk</td>
<td>YES</td>
<td>bit</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>ProjectCompletedError</td>
<td>YES</td>
<td>bit</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>ByWorker</td>
<td>YES</td>
<td>bit</td>
<td><p>True - Папка на машине Робота</p>
<p>False - Сетевая шара</p></td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>ShareFolder</td>
<td>YES</td>
<td>nvarchar</td>
<td>Сетевая шара</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>LockAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Блокировка (служебное поле), чтобы одновременно несколько инстансов
не поставили в очередь выполнение проекта задания этого триггера</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>NodeLock</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, заблокировавшей триггер в БД</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>Version</td>
<td>NO</td>
<td>int</td>
<td>Служебное поле для разруливания конкурентного доступа</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>IncomingFrom</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>IncomingSubject</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>IncomingEmailIntevalInSeconds</td>
<td>YES</td>
<td>int</td>
<td>Интервал запросов к почтовому серверу</td>
</tr>
<tr class="odd">
<td><ol start="25" type="1">
<li></li>
</ol></td>
<td>IncomingEmailWindowSize</td>
<td>YES</td>
<td>int</td>
<td>Максимальное количество писем, забираемых за один раз</td>
</tr>
<tr class="even">
<td><ol start="26" type="1">
<li></li>
</ol></td>
<td>ChangeType</td>
<td>YES</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="27" type="1">
<li></li>
</ol></td>
<td>FullPath</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="28" type="1">
<li></li>
</ol></td>
<td>OldFullPath</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="29" type="1">
<li></li>
</ol></td>
<td>WatcherFilter</td>
<td>YES</td>
<td>nvarchar</td>
<td>Фильтр для содержимого папки</td>
</tr>
<tr class="even">
<td><ol start="30" type="1">
<li></li>
</ol></td>
<td>FiredAtEmail</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания от получения новых писем</td>
</tr>
<tr class="odd">
<td><ol start="31" type="1">
<li></li>
</ol></td>
<td>FromRobotId</td>
<td>YES</td>
<td>int</td>
<td>Робот, который зажег триггер</td>
</tr>
<tr class="even">
<td><ol start="32" type="1">
<li></li>
</ol></td>
<td>CountNewExchangeQueueItems</td>
<td>YES</td>
<td>int</td>
<td>Количество новых элементоы очереди, при наличии которого сработает
триггер</td>
</tr>
<tr class="odd">
<td><ol start="33" type="1">
<li></li>
</ol></td>
<td>CronString</td>
<td>YES</td>
<td>nvarchar</td>
<td>Крон-строка расписания, по которой происходит запуск опроса
очереди</td>
</tr>
<tr class="even">
<td><ol start="34" type="1">
<li></li>
</ol></td>
<td>Interval</td>
<td>YES</td>
<td>int</td>
<td>Интервал опроса в минутах</td>
</tr>
<tr class="odd">
<td><ol start="35" type="1">
<li></li>
</ol></td>
<td>FiredAtNewItems</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата срабатывания от наличия в очереди новых элементов</td>
</tr>
<tr class="even">
<td><ol start="36" type="1">
<li></li>
</ol></td>
<td>Tags</td>
<td>YES</td>
<td>nvarchar</td>
<td>Строка тэгов, через запятую. Если заданы, то только на элементы с
данными тэгами будет триггериться</td>
</tr>
<tr class="odd">
<td><ol start="37" type="1">
<li></li>
</ol></td>
<td>HardKill</td>
<td>YES</td>
<td>bit</td>
<td>Если установлено и True - принудительная остановка робота с
проектом; Если установлено и False - поднять флаг мягкой остановки</td>
</tr>
</tbody>
</table>

## UserRobotQuotas

Квота пользователя на лицензии робота

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 23%" />
<col style="width: 16%" />
<col style="width: 12%" />
<col style="width: 40%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>UserId</td>
<td>NO</td>
<td>nvarchar</td>
<td>Идентификатор пользователя из БД ltoolsidentity</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>EnterpriseRobotQuota</td>
<td>YES</td>
<td>int</td>
<td>Квота на Enterprise лицензии</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>StandardRobotQuota</td>
<td>YES</td>
<td>int</td>
<td>Квота на Standard лицензии</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>DesktopRobotQuota</td>
<td>YES</td>
<td>int</td>
<td>Квота на Desktop лицензии</td>
</tr>
</tbody>
</table>

## UserSystemEventTypes

Тип события, на которое может подписаться пользователь, чтобы приходили
уведомления

<table style="width:100%;">
<colgroup>
<col style="width: 7%" />
<col style="width: 31%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>EventType</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>UserId</td>
<td>YES</td>
<td>nvarchar</td>
<td></td>
</tr>
</tbody>
</table>

## UserUISettings

Клиентские настройки для пользователя

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 24%" />
<col style="width: 19%" />
<col style="width: 15%" />
<col style="width: 34%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>UserName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Имя пользователя</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>Settings</td>
<td>YES</td>
<td>nvarchar</td>
<td>Строка данных с настройками</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>-</td>
</tr>
</tbody>
</table>

## WorkerIpAddresses

IP-адреса машин Роботов, которые агенты сообщили Оркестратору

<table>
<colgroup>
<col style="width: 6%" />
<col style="width: 25%" />
<col style="width: 20%" />
<col style="width: 15%" />
<col style="width: 30%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Key</td>
<td>NO</td>
<td>nvarchar</td>
<td>Идентификатор машины</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>IpAddress</td>
<td>NO</td>
<td>nvarchar</td>
<td>IP-адрес</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>CreatedAt</td>
<td>NO</td>
<td>datetime2</td>
<td>Дата создания записи</td>
</tr>
</tbody>
</table>

## WorkerNoRdpPeriods

Периоды "простоя" машины роботов - когда не поднята ни одна RDP-сессия
для оркестраторных роботов (учитываются только сессии, поднятые службой
RDP2)

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 18%" />
<col style="width: 14%" />
<col style="width: 17%" />
<col style="width: 43%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>uniqueidentifier</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>IsPauseFlag</td>
<td>YES</td>
<td>bit</td>
<td>Признак техперерыва для службы RDP2</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>StartededAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время начала периода простоя.; Включает погрешность в один шаг
работы службы RDP2 (по умолчанию 5 сек.)</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>StoppeddAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата/время завершения простоя.; Включает погрешность в один шаг
работы службы RDP2 (по умолчанию 5 сек.)</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>WorkerId</td>
<td>NO</td>
<td>int</td>
<td>Идентификатор машины роботов</td>
</tr>
</tbody>
</table>

## Workers

Машина робота

<table>
<colgroup>
<col style="width: 5%" />
<col style="width: 32%" />
<col style="width: 12%" />
<col style="width: 12%" />
<col style="width: 36%" />
</colgroup>
<thead>
<tr class="header">
<th><p>№</p>
<p>п/п</p></th>
<th>Наименование поля</th>
<th>Допускает NULL</th>
<th>Тип данных</th>
<th>Описание</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><ol type="1">
<li></li>
</ol></td>
<td>Id</td>
<td>NO</td>
<td>int</td>
<td></td>
</tr>
<tr class="even">
<td><ol start="2" type="1">
<li></li>
</ol></td>
<td>Name</td>
<td>YES</td>
<td>nvarchar</td>
<td>Произвольное наименование</td>
</tr>
<tr class="odd">
<td><ol start="3" type="1">
<li></li>
</ol></td>
<td>IpAddress</td>
<td>YES</td>
<td>nvarchar</td>
<td>IP или DNS</td>
</tr>
<tr class="even">
<td><ol start="4" type="1">
<li></li>
</ol></td>
<td>AdminName</td>
<td>YES</td>
<td>nvarchar</td>
<td>Логин администратора</td>
</tr>
<tr class="odd">
<td><ol start="5" type="1">
<li></li>
</ol></td>
<td>AdminPassword</td>
<td>YES</td>
<td>nvarchar</td>
<td>Пароль администратора</td>
</tr>
<tr class="even">
<td><ol start="6" type="1">
<li></li>
</ol></td>
<td>Disabled</td>
<td>NO</td>
<td>bit</td>
<td>Принзак логического удаления</td>
</tr>
<tr class="odd">
<td><ol start="7" type="1">
<li></li>
</ol></td>
<td>TestSucceededDate</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата тестирования доступности рабочей машины</td>
</tr>
<tr class="even">
<td><ol start="8" type="1">
<li></li>
</ol></td>
<td>TestSucceeded</td>
<td>YES</td>
<td>bit</td>
<td>Результат тестирования доступности рабочей машины</td>
</tr>
<tr class="odd">
<td><ol start="9" type="1">
<li></li>
</ol></td>
<td>NoSuccesRaiseDate</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата начала недоступности. Как становится доступной, эта дата
обнуляется</td>
</tr>
<tr class="even">
<td><ol start="10" type="1">
<li></li>
</ol></td>
<td>Notificated</td>
<td>YES</td>
<td>bit</td>
<td>Событие доступности/недоступности отправлено</td>
</tr>
<tr class="odd">
<td><ol start="11" type="1">
<li></li>
</ol></td>
<td>TenantId</td>
<td>YES</td>
<td>nvarchar</td>
<td>Идентификатор тенанта</td>
</tr>
<tr class="even">
<td><ol start="12" type="1">
<li></li>
</ol></td>
<td>MaxSimulRobotCount</td>
<td>YES</td>
<td>int</td>
<td>Максимальное количество одновременно работающих роботов</td>
</tr>
<tr class="odd">
<td><ol start="13" type="1">
<li></li>
</ol></td>
<td>CurrentSimulRobotCount</td>
<td>NO</td>
<td>int</td>
<td>Текущее количество одновременно работающих роботов</td>
</tr>
<tr class="even">
<td><ol start="14" type="1">
<li></li>
</ol></td>
<td>IsRunning</td>
<td>NO</td>
<td>bit</td>
<td>Признак вкл/выключенного Агента, выключенный Агент отличается от
недоступного и не участвует в опросах машин роботов,; в лог не пишутся
сообщения о недоступности.</td>
</tr>
<tr class="odd">
<td><ol start="15" type="1">
<li></li>
</ol></td>
<td>MemoryPrcnt</td>
<td>YES</td>
<td>numeric</td>
<td>% RAM (среднее значение из полученной пачки); Собирается из метрик
производительности при опросе состояния машины робота</td>
</tr>
<tr class="even">
<td><ol start="16" type="1">
<li></li>
</ol></td>
<td>LoadingDynamicAt</td>
<td>YES</td>
<td>datetime2</td>
<td>Дата фиксации информации о динамике нагрузки.; Проставляется при
получении метрик производительности при опросе состояния машины робота,;
если нагрузка существенно поменялась. Используется для определения
факта, что текущая нагрузка; держится достаточно долго в некотором
диапазоне</td>
</tr>
<tr class="odd">
<td><ol start="17" type="1">
<li></li>
</ol></td>
<td>LoadingDynamic</td>
<td>YES</td>
<td>int</td>
<td>Динамика нагрузки; Вычисляется при опросе состояния машины робота и
текущих зафиксированных параметров нагрузки</td>
</tr>
<tr class="even">
<td><ol start="18" type="1">
<li></li>
</ol></td>
<td>CPUPrcnt</td>
<td>YES</td>
<td>numeric</td>
<td>% CPU (среднее значение из полученной пачки); Собирается из метрик
производительности при опросе состояния машины робота</td>
</tr>
<tr class="odd">
<td><ol start="19" type="1">
<li></li>
</ol></td>
<td>NoRdpPauseDurationInSeconds</td>
<td>YES</td>
<td>int</td>
<td>Длительность паузы без сессий роботов (оркестраторных).</td>
</tr>
<tr class="even">
<td><ol start="20" type="1">
<li></li>
</ol></td>
<td>NeedNoRdpPause</td>
<td>YES</td>
<td>bit</td>
<td>Флаг поднимается если нужно устроить "паузу" на машине без сессий
роботов (оркестраторных).; Флаг сбрасывается автоматически после начала
паузы.</td>
</tr>
<tr class="odd">
<td><ol start="21" type="1">
<li></li>
</ol></td>
<td>IsNoRdpPause</td>
<td>YES</td>
<td>bit</td>
<td>Флаг поднимается автоматические если установлен NeedNoRdpPause и на
сервере нет активных сессий роботов (оркестраторных); Флаг сбрасывается
автоматически по истечении паузы (длительность задается в
NoRdpPauseDurationInSeconds).</td>
</tr>
<tr class="even">
<td><ol start="22" type="1">
<li></li>
</ol></td>
<td>NodeId</td>
<td>YES</td>
<td>int</td>
<td>Идентификатор ноды, которая меняла запись</td>
</tr>
<tr class="odd">
<td><ol start="23" type="1">
<li></li>
</ol></td>
<td>Linux</td>
<td>YES</td>
<td>bit</td>
<td>Linux-машина</td>
</tr>
<tr class="even">
<td><ol start="24" type="1">
<li></li>
</ol></td>
<td>AgentVersion</td>
<td>YES</td>
<td>nvarchar</td>
<td>Версия Агента, которую агент отдает при его опросе</td>
</tr>
</tbody>
</table>

# **Оглавление**

[**Описание структуры БД ltools**
[1](#описание-структуры-бд-ltools)](#описание-структуры-бд-ltools)

[\_\_EFMigrationsHistory
[1](#efmigrationshistory)](#efmigrationshistory)

[Agents [1](#agents)](#agents)

[Assets [2](#assets)](#assets)

[AssetRobots [3](#assetrobots)](#assetrobots)

[Assignments [3](#assignments)](#assignments)

[AssignmentSchedulerSignalNodeConfirms
[4](#assignmentschedulersignalnodeconfirms)](#assignmentschedulersignalnodeconfirms)

[AssignmentVariables [5](#assignmentvariables)](#assignmentvariables)

[BlackWhiteIpStudioRules
[5](#blackwhiteipstudiorules)](#blackwhiteipstudiorules)

[BusyRobotLicenseItems
[5](#busyrobotlicenseitems)](#busyrobotlicenseitems)

[BusyRobotLicenses [6](#busyrobotlicenses)](#busyrobotlicenses)

[BusyStudioLicenses [6](#busystudiolicenses)](#busystudiolicenses)

[ConfigHash [6](#confighash)](#confighash)

[CurrentSystemParameters
[6](#currentsystemparameters)](#currentsystemparameters)

[DeployTemplates [6](#deploytemplates)](#deploytemplates)

[ExchangeQueueRobotPermissions
[7](#exchangequeuerobotpermissions)](#exchangequeuerobotpermissions)

[ExchangeQueues [7](#exchangequeues)](#exchangequeues)

[ExchangeQueueStatisticAvgs
[9](#exchangequeuestatisticavgs)](#exchangequeuestatisticavgs)

[ExchangeQueueStatistics
[10](#exchangequeuestatistics)](#exchangequeuestatistics)

[ExchangeQueueValueEvents
[10](#exchangequeuevalueevents)](#exchangequeuevalueevents)

[ExchangeQueueValueMetadata
[11](#exchangequeuevaluemetadata)](#exchangequeuevaluemetadata)

[ExchangeQueueValuePrefetchReadeds
[11](#exchangequeuevalueprefetchreadeds)](#exchangequeuevalueprefetchreadeds)

[ExchangeQueueValues [11](#exchangequeuevalues)](#exchangequeuevalues)

[ExchangeQueueValueTags
[13](#exchangequeuevaluetags)](#exchangequeuevaluetags)

[ExchangeQueueValuesRobotLocks
[14](#exchangequeuevaluesrobotlocks)](#exchangequeuevaluesrobotlocks)

[FolderObjects [14](#folderobjects)](#folderobjects)

[FolderObjects2 [14](#folderobjects2)](#folderobjects2)

[Folders [15](#folders)](#folders)

[Folders2 [15](#folders2)](#folders2)

[FolderUsers [15](#folderusers)](#folderusers)

[FolderUsers2 [16](#folderusers2)](#folderusers2)

[GeneralSettings [16](#generalsettings)](#generalsettings)

[IncomingEmailLogs [17](#incomingemaillogs)](#incomingemaillogs)

[IncomingEmails [17](#incomingemails)](#incomingemails)

[IncomingEmailWindowLogs
[18](#incomingemailwindowlogs)](#incomingemailwindowlogs)

[IPv4Addresses [18](#ipv4addresses)](#ipv4addresses)

[IPv4Masks [19](#ipv4masks)](#ipv4masks)

[LoadTests [19](#loadtests)](#loadtests)

[LoadTestScheduleItemActiveRobots
[19](#loadtestscheduleitemactiverobots)](#loadtestscheduleitemactiverobots)

[LoadTestScheduleItemActives
[20](#loadtestscheduleitemactives)](#loadtestscheduleitemactives)

[LoadTestScheduleItems
[20](#loadtestscheduleitems)](#loadtestscheduleitems)

[LoadTestSchedules [20](#loadtestschedules)](#loadtestschedules)

[LoadTestScopes [21](#loadtestscopes)](#loadtestscopes)

[LoadTestScopeSchedulerSignalNodeConfirms
[21](#loadtestscopeschedulersignalnodeconfirms)](#loadtestscopeschedulersignalnodeconfirms)

[LoadTestScopeTriggers
[21](#loadtestscopetriggers)](#loadtestscopetriggers)

[LogsDump [22](#logsdump)](#logsdump)

[Nodes [22](#nodes)](#nodes)

[NuGetTasks [23](#nugettasks)](#nugettasks)

[ProductionCalendars [23](#productioncalendars)](#productioncalendars)

[ProductionCalendar2 [23](#productioncalendar2)](#productioncalendar2)

[ProductionCalendar2Items
[24](#productioncalendar2items)](#productioncalendar2items)

[Rdp2AddressFilters [24](#rdp2addressfilters)](#rdp2addressfilters)

[RobotAgentSessions [24](#robotagentsessions)](#robotagentsessions)

[RobotDeployTrackings
[24](#robotdeploytrackings)](#robotdeploytrackings)

[RobotDistrExistsNodeConfirms
[25](#robotdistrexistsnodeconfirms)](#robotdistrexistsnodeconfirms)

[RobotDistrs [25](#robotdistrs)](#robotdistrs)

[RobotGroupItems [26](#robotgroupitems)](#robotgroupitems)

[RobotGroups [26](#robotgroups)](#robotgroups)

[Robots [26](#robots)](#robots)

[RobotSoftKillSignals
[28](#robotsoftkillsignals)](#robotsoftkillsignals)

[RobotStartTrackings [28](#robotstarttrackings)](#robotstarttrackings)

[RobotUnlockQueue [28](#robotunlockqueue)](#robotunlockqueue)

[RolePermissions [29](#rolepermissions)](#rolepermissions)

[RootFolderUsers2 [29](#rootfolderusers2)](#rootfolderusers2)

[RpaProjectArchiveExistsNodeConfirms
[29](#rpaprojectarchiveexistsnodeconfirms)](#rpaprojectarchiveexistsnodeconfirms)

[RpaProjectArchives [29](#rpaprojectarchives)](#rpaprojectarchives)

[RpaProjectLaunches [30](#rpaprojectlaunches)](#rpaprojectlaunches)

[RpaProjectLaunchVariables
[31](#rpaprojectlaunchvariables)](#rpaprojectlaunchvariables)

[RpaProjectQueue [32](#rpaprojectqueue)](#rpaprojectqueue)

[RpaProjectRobots [33](#rpaprojectrobots)](#rpaprojectrobots)

[RpaProjectTags [33](#rpaprojecttags)](#rpaprojecttags)

[RpaProjectWorkflows [33](#rpaprojectworkflows)](#rpaprojectworkflows)

[RpaProjects [33](#rpaprojects)](#rpaprojects)

[RpaProjectVariables [35](#rpaprojectvariables)](#rpaprojectvariables)

[RpaProjectVariableTemps
[35](#rpaprojectvariabletemps)](#rpaprojectvariabletemps)

[Schedules [35](#schedules)](#schedules)

[StatesSlaConfig [36](#statesslaconfig)](#statesslaconfig)

[Tags [36](#tags)](#tags)

[Tenants [36](#tenants)](#tenants)

[Triggers [37](#triggers)](#triggers)

[UserRobotQuotas [39](#userrobotquotas)](#userrobotquotas)

[UserSystemEventTypes
[39](#usersystemeventtypes)](#usersystemeventtypes)

[UserUISettings [39](#useruisettings)](#useruisettings)

[WorkerIpAddresses [40](#workeripaddresses)](#workeripaddresses)

[WorkerNoRdpPeriods [40](#workernordpperiods)](#workernordpperiods)

[Workers [40](#workers)](#workers)

[1] Здесь и далее системные таблицы использовать пользователю запрещено.
За исключением согласованных с Вендором случаев. Иначе это может
привести к краху системы

[2] Название таблицы оставлено для совместимости, не соответствует её
использованию

[3] Зарезервировано

[4] Зарезервировано

[5] Зарезервировано

[6] Зарезервировано

[7] Зарезервировано

[8] Зарезервировано

[9] Зарезервировано

[10] Зарезервировано

[11] Зарезервировано

[12] Зарезервировано

[13] Зарезервировано


