# Задания

Задания – это основной инструмент автоматизации запуска RPA-проектов. Задания бывают с ручным запуском и с запуском по триггеру. 

Для проектов, которые имеют входные/выходные аргументы, задания позволяют задать/получить значения этих аргументов для каждого запуска. Такие проекты можно запускать только через задания.

Задания создаются на вкладке **Задания/Все задания** по кнопке **Добавить задание**:

![](../../../../orchestrator-new/resources/orchestrator-user/tasks/tasks-overview1.PNG)

## Триггеры

Всего имеется 7 типов триггеров для заданий:

| №п/п | Наименование | Описание | Параметры |
| --- | --- | --- | --- |
| 1. | Запуск по расписанию | Срабатывает по фиксированному расписанию | Расписание, заданное Cron-строкой или конструктором. Расписание должно быть предварительно задано в справочнике расписаний.Может быть сконфигурировано как мягкое или принудительное закрытие робота (галочка «Завершение робота»), если в данный момент робот выполняется по заданию.Триггер с галочкой «Завершение робота» можно рассматривать как предохранитель. Он всегда должен идти в паре с обычным триггером, который запускает робота, иначе не имеет смысла. Допустим, робот работает ~10 минут. Но, может иногда работать дольше планируемого. Тогда его можно запускать каждые 15 минут и через 10 минут завершать по триггеру – 2 расписания «каждые 15 минут», сдвинутые на 10 минут относительно друг друга, второй триггер с этой галочкой |
| 2. | Запуск при получении Email | Срабатывает при поступлении в заранее настроенный ящик входящей почты письма | Ящик входящей почты, отправитель письма, тема письма |
| 3. | Запуск при\* изменении очереди обмена данными | Срабатывает при добавлении в очередь нового элемента | Очередь обмена данными |
| 4. | Запуск при изменении папки | Бывает двух типов: для папки на машине робота или для сетевой папкиСрабатывает при изменении содержимого папки: добавлении/изменении/удалении файлов | Для папки на машине робота: машина робота и абсолютный путь к папкеДля сетевой папки: UNC-имя папки. Папки должны быть настроены заранее |
| 5. | Запуск при завершении проекта Роботом | Срабатывает при завершении проекта каким-либо роботом | RPA-проект, результат завершения (с ошибкой или без ошибки) |
| 6. | Запуск из другого робота | Срабатывает при прямом вызове запуска триггера из робота |  |
| 7. | Запуск при наличии новых элементов в очереди обмена данными | Срабатывает, когда при очередном опросе очереди в ней появляются новые элементы | Очередь обмена данными, периодичность опроса, количество новых элементов |

>\* - *Исключен. Рекомендуется использовать тип **Запуск при наличии новых элементов в очереди обмена данными***

Триггеры позволяют запускать RPA-проекты по событию (подписка на события), образовывая реактивные цепочки исполнения, и/или периодическое исполнение RPA-проектов.

На иллюстрации ниже задание 1 имеет сразу 2 триггера – запуск по расписанию и запуск при получении Email. 
Триггер на получение Email может использоваться, например, для внепланового удаленного запуска проекта. 
* В процессе выполнения проекта задания 1 происходит запись в очередь обмена данными Queue1, на изменение которой подписано задание 2. 
* В процессе выполнения проекта задания 2 происходит запись в папку C:\tmp на машине робота, на изменение которой подписано задание 3. 
* По завершению выполнения проекта задания 3 запустится проект задания 4, так как задание 4 подписано на завершение проекта задания 3.

![](../../../../orchestrator-new/resources/orchestrator-user/tasks/tasks-overview2.PNG)

Одному заданию можно назначить одновременно несколько триггеров. При этом стоит следить, чтобы триггеры не вступали в логическое противоречие для RPA-проекта задания. акже стоит следить, чтобы триггеры не вступали в логическое противоречие для разных заданий.

Не рекомендуется при создании триггеров по расписанию использовать одинаковые, или кратные расписания, которые ведут к одновременному запуску роботов. 
Полностью одновременного запуска все равно не получится, но нагрузка на систему в такие моменты может лавинообразно вырасти. 

Например, если есть три расписания *Каждые 15 минут*, *Каждые 30 минут* и *Каждый час*, лучше в последних двух заменить на *Каждые 30 минут и одна секунда* и *Вторая секунда каждого часа*. 
Это существенно снизит потребление ресурсов при запуске роботов, и фактически не отразится на «логической одновременности».

Если создается задание с триггером **Запуск по расписанию**, то расписание нужно выбрать из справочника ранее созданных расписаний. Расписание добавляется в справочник на вкладке **Задания/Расписания**.
Расписание может быть согласовано с производственным календарем. Если используются множественные производственные календари (задается администратором глобально в конфигурационном файле), то с каждым расписанием можно связывать индивидуальный производственный календарь. Множественных производственных календарей можно создать несколько на один год, например, календарь, в котором нет новогодних праздников.

Для работы триггера **Запуск при получении Email** должен быть задан минимум один почтовый ящик для тенанта (в настройках тенанта) для входящей почты. Дополнительные ящики могут быть добавлены на вкладке **Настройки/Email для входящей почты**.  

В версии 1.25.1 Оркестратора в форму добавления триггера **Запуск при получении Email** был добавлен чекбокс *Оповестить автора(ов) письма*. При его активации осуществляется оповещение отправителей, указанных в поле "От" в случае успешного/неуспешного выполнения проекта, а также ошибки старта робота. 
При этом при срабатывании этого конкретного триггера другим подписчикам рассылка по указанным событиям приходить не будет.

Также в версии 1.25.1 в форму создания/редактирования задания с триггером **Запуск при получении Email** было добавлено поле *Ресурс* с выпадающим списком доступных ресурсов типа `jObject`. Пользователь может выбрать один ресурс, в который при срабатывании триггера будет записано письмо в формате JSON: адрес, отправитель, тема письма и текстовое тело письма.

Кроме того, в версии 1.25.1 добавлено ограничение количества писем в email-триггере **(IMAP)**. Ранее такая функциональность была доступна только для POP3 и Exchange. 
Теперь в UI можно задать лимит писем, обрабатываемых за одно срабатывание триггера.

Для работы триггера **Запуск при изменении папки** на машине робота должна быть задана стратегия выполнения проектов, разрешающая выполнение проекта на привязанных к нему роботах, и к проекту должны быть привязаны развёрнутые на данной машине роботы.

При помощи кнопок управления **Запустить/Остановить** задание запускается/ставится на паузу. Ставить на паузу можно только задание, выполняющееся по срабатыванию триггера.
Запуск задания означает, что RPA-проект задания будет поставлен в очередь на выполнение. Для разового задания это произойдет сразу при запуске. Для задания по срабатыванию триггера – каждый раз при срабатывании триггера. В поле **Состояние** отображается именно состояние самого задания, не робота. Активных роботов в этот момент может не быть, а проект задания может быть помещен на ожидание в очередь.

В версии 1.25.1 была обновлена логика отображения кнопок **"Остановить все"** и **"Запустить все остановленные"**:
   - Теперь видимость кнопок определяется только у пользователей, которым администратор назначил соответствующие права.
   - Для встроенных ролей **Администратор** и **Администратор тенанта** права на эти операции предоставлены по умолчанию.
   - Добавлены события в журнал Оркестратора для логирования массовых операций: 
      - **"Старт остановки всех запущенных заданий"**.
      - **"Старт возобновления всех ранее остановленных заданий".**
   - Логируются также события о конкретных заданиях, остановленных или возобновленных в результате массовых операций.

Наблюдать за процессом запуска робота можно также на вкладке **Роботы/Все роботы** и **Мониторинг**.

Информация о последнем выполняющим по заданию проект роботе отображается в поле **История выполнения**.

При срабатывании триггера задания его RPA-проект ставится в очередь выполнения. И если есть подходящий для выполнения робот – выполняется этим роботом. Если нет – RPA-проект находится в очереди, пока не будет обработан или удален из неё вручную. 

Такие общие параметры системы как *время срабатывания задания*, *количество роботов*, *количество заданий* и *количество лицензий* должны быть согласованы. Иначе возможна ситуация – при нехватке свободных роботов/лицензий – когда очередь проектов на выполнение будет только неконтролируемо расти. Фактически – это отказ в обслуживании, очередь нужно будет принудительно чистить вручную.

Если RPA-проект связан с роботом, через задание образуется связь **Задание-Проект-Робот**, которая гарантирует, что проект запустится на нужном роботе. 

У проекта могут создаваться версии, одна из которых всегда активная. Активная – это значит задание будет запускать именно эту версию проекта.

![](../../../../orchestrator-new/resources/orchestrator-user/tasks/tasks-overview3.PNG)
