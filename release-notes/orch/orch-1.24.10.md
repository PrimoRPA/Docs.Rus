# Primo RPA Orchestrator 1.24.10

Изменения  **Primo RPA Orchestrator** за октябрь 2024-го года. 

## Обновления и улучшения

1. Добавлена возможность редактирования встроенных системных ролей **Robot** и **Studio** для привязки к AD-группам.

1. В шаблоне развертывания Оркестратора добавлен переключатель **Не отправлять логи в Оркестратор**. При его активации робот не отправляет логи, за исключением событий: старт и завершение робота, а также логи, связанные с файлами блокировок.

3. Добавлен фильтр по *TenantId** в мониторинг Оркестратора, который позволяет отображать данные роботов только выбранного тенанта. 

4. Добавлена информация в рассылку по событиям, связанным с лицензиями, роботами и заданиями. Теперь в письмах содержатся следующие данные:
   - Имя робота
   - Название и IP-адрес машины робота
   - Название проекта и его версия
   - Название задания

Эти данные доступны при условии, что в интерфейсе Оркестратора в разделе **Настройки → Пользователи** в форме добавления/редактирования пользователя указаны поля **"Email" и "События"** (выбрано "Все события").

5. Добавлено ограничение на количество попыток ввода неверного текущего пароля при смене пароля: после 3-й неудачной попытки требуется перезайти в сессию для продолжения.

7. Реализована возможность контроля и отслеживания изменений конфигурационных файлов служб Оркестратора в журнале (вкладка "Информационная безопасность"). При изменении конфигурации появляется событие `Конфигурационный файл изменен`, с возможностью просмотра и сохранения предыдущих версий файлов через гиперссылку в полных сведениях о событии.

8. В конфигурацию WebApi в секцию `Serilog` добавлен параметр `rollOnFileSizeLimit`, который создает новый файл лога при достижении размера 1 Гб. Это помогает управлять объемом логов в высоконагруженных системах. Необходимо установить значение true для активации этой функции.

9. В конфигурационный файл WebApi добавлен параметр `Secrets:ConnectionString`. В случае его отсутствия используется переменная окружения `SecretsConnection`.

10. В конфигурационный файл WebApi добавлены параметры:  
- `"AdminPasswordMaxLength"`: 128 в секции Worker — задает максимальную длину пароля для администратора машины Агента.
- `"RdpUserPasswordMaxLength"`: 128 в секции RDP — задает максимальную длину пароля для RDP-пользователя.
    
## Исправленные ошибки 

1. Устранена ошибка, при которой запускались дублирующие фоновые службы. Теперь запускается только одна служба, согласно настройкам конфигурации Оркестратора
1. Исправлена ошибка, из-за которой роль *Администратор тенанта* не отображалась в выпадающем списке при создании нового пользователя. Теперь данная роль доступна для выбора согласно настройкам системы.

## Улучшения служб Agent и RDP2

1. Обновлен Primo Agent до версии 1.24.1.8 с исправлениями уязвимостей для повышения безопасности системы.

1. Добавлены расширенные фильтры для службы RDP2, позволяющие тонко масштабировать сессии внутри машин роботов. 

1. Исправлена ошибка, при которой служба RDP2 не восстанавливала сессии из-за сбоя связи с Оркестратором. Теперь сессии автоматически возобновляются после восстановления соединения.

1. В конфигурационный файл службы Агента добавлен новый параметр `CheckLogoutResult=true`, который позволяет включить проверку успешного завершения сессии пользователя после выполнения команды `Logoff`. При активации параметра система проверяет, что сессия не остается активной на сервере после разлогинивания. При некорректном завершении сессии в логах будет отображено сообщение: `Session {userName} pseudo logout detected`.

 ## Обновления и улучшения Веб-интерфейса 2.22.0
 
1. Добавлен параметр `Windows-авторизация` с отметкой "Только для Windows-роботов"  в шаблонах развертывания. При включении этого параметра робот будет авторизоваться через Windows/AD под учетной записью RDP-сессии. Если параметр отключен, робот использует локальную учетную запись Оркестратора (обычно системную учетную запись "robot"). 
2. Добавлен параметр **Запуск с повышенными правами (UseHighestTaskRunLevel)** на странице добавления/редактирования проекта. При включении этого флага робот запускается с активированным параметром `Run with highest privileges` в Планировщике задач Windows. По умолчанию флаг отключен.
3. Добавлены диалоговые окна с подтверждением для кнопок *Остановить все* и *Запустить все остановленные*. Теперь перед выполнением этих действий пользователю будет предложено подтвердить операцию, аналогично операциям удаления.
4. Окно **Активные пользователи** на главной странице теперь скрыто для всех пользователей, кроме администраторов и тенант-администраторов.

5. Улучшен интерфейс: 
 - Стилизованы разделы с вкладками, добавлены стили для темной темы.
 - Настройка темы перемещена в главное меню.
 - Добавлены подсказки для пользователей на главной странице.

6. Добавлено поле `Текущий пароль` в форме *Смена пароля* . Поле доступно во всех темах и при выборе английского языка. Пароль не обновляется, если поле не заполнено.
7. Исправлена ошибка на странице *Аргументы проекта*, из-за которой в истории запусков не обновлялись аргументы для выбранной даты. 
8. Исправлена ошибка, из-за которой роль *Администратор тенанта* не отображалась в выпадающем списке при создании нового пользователя. Теперь данная роль доступна для выбора согласно настройкам системы.

## Где найти

[*Скачать Primo RPA Orchestrator*](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FOrchestrator)
Полный архив с необходимыми файлами для установки и настройки Оркестратора

[*Скачать дистрибутив Primo RPA Robot Enterprise*](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FRelease%2FRobot). 
Архивы дистрибутивов доступны в нескольких версиях, в зависимости от архитектуры вашего оборудования и операционной системы. Эти дистрибутивы предназначены для загрузки и использования непосредственно в Оркестраторе.

Если у вас возникнут сложности с установкой или использованием данной версии, пожалуйста, обращайтесь к вашему менеджеру или в [наш чат поддержки в Telegram](https://t.me/primo_RPA_chat).
