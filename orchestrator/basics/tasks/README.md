# Задания

Задания – это основной инструмент автоматизации запуска RPA-проектов. Автоматический запуск наступает при срабатывании выбранного триггера.

Задание также может запускаться вручную, если триггер не задан.

## Виды триггеров

Триггеры позволяют запускать RPA-проекты по событию, образуя реактивные цепочки исполнения и/или периодическое исполнение проектов. Ниже перечислены доступные виды триггеров.

### 1. Запуск по расписанию
Проект, указанный в задании, будет запускаться автоматически при наступлении времени из расписания. Данный триггер можно настроить не только на запуск, но и на завершение заданий по расписанию.

Параметры триггера:

![](<../../../.gitbook/assets/триггер по расписанию-2.png>)

* **Использовать готовое** — обязательный параметр. Готовое расписание, заданное Cron-строкой или конструктором. Чтобы пользователь мог видеть список доступных расписаний, их следует предварительно добавить в [справочник расписаний](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/tasks/schedules). 
* **Завершение робота** — определяет, нужно ли принудительно, по расписанию, завершать запущенное задание. По умолчанию чекбокс выключен — принудительное завершение задания не используется. 

Чекбокс **Завершение робота** играет в задании роль предохранителя. Допустим, робот выполняет задание ~10 минут, но иногда может и дольше. В этом случае можно запускать его каждые 15 минут — это первый триггер, и через 10 минут завершать по второму триггеру. 
Таким образом, в одном задании мы будем иметь 2 триггера по расписанию: 
* В первом выбрано расписание «каждые 15 минут», которое запускает робота с заданием. 
* Во втором выбрано расписание «каждые 15 минут», но сдвинутое на 10 минут относительно первого — оно будет завершать задание, если робот его еще выполняет. Во втором триггере включен чекбокс **Завершение робота**.

#### Как создать задание с завершением
Создаем задание с двумя триггерами **Запуск по расписанию**:
1. Первый триггер предназначен для запуска задания:
   * Выбираем расписание в параметре **Использовать готовое**. По нему задание будет запускаться.
   * Чекбокс **Завершение робота** оставляем отключенным. 
2. Второй триггер управляет завершением задания:
   * Выбираем расписание в параметре **Использовать готовое**. По нему задание будет остановлено в случае, если еще выполняется.
   * Включаем чекбокс **Завершение робота** и выбираем, как следует остановить робота — мягко или принудительно:
     * Если мягко — выбираем **Попросить остановиться**. Мягкая остановка позволяет избежать потенциальных ошибок. Чтобы остановка сработала, в RPA-проект обязательно помещаем элемент [**Должен остановиться**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_process/el_shouldstop) (Should stop).
     * Если принудительно — выбираем значение **Принудительное**. В этом случае в проекте не требуется наличие элемента **Должен остановиться**.
3. Сохраняем задание.

  
### 2. Запуск при получении Email
Триггер срабатывает при поступлении письма в ящик входящей почты. Предварительно следует задать минимум один почтовый ящик тенанта для входящей почты. Он указывается системным администратором в [настройках тенанта](https://docs.primo-rpa.ru/primo-rpa/orchestrator/deployment/tenants) в конфиг-файле. 

Дополнительные ящики могут быть добавлены на вкладке [Настройки > Email для входящей почты](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/register-robot/email). Для добавления пользователь должен обладать правами администратора (глобальными или в рамках тенанта).

Параметры триггера:

![](<../../../.gitbook/assets/триггер по email-1.png>)

* **Email** — ящик входящей почты, из которого будут прочитаны последние входящие письма. Обязательный параметр.
* **От** — отправитель письма. Необязательный.
* **Тема** — тема письма. Необязательный.

### 3. Запуск при наличии новых элементов в очереди обмена данными
Срабатывает, когда при очередном опросе очереди в ней появляются новые элементы. Триггер действует асинхронно с добавлением элементов - время опроса очереди настраивается в параметрах.

Параметры:

![](<../../../.gitbook/assets/триггер по новым элементам очереди-1.png>) 

* **Очередь обмена данными** — обязательный параметр. Выберите название очереди из выпадающего списка.
* **Периодичность опроса очереди** — обязательно. Указывается в виде Cron-строки расписания опроса или интервала опроса в минутах.
* **Количество новых элементов очереди**:
  * Если мы указываем в значении число N, то триггер сработает, когда при опросе очереди в ней будет не менее N новых элементов. Например, если указано 5, то триггер сработает, когда в очереди будет 5 и более новых элементов. Но не меньше 5.
  * Если мы не заполняем этот параметр, то по умолчанию считается, что нам не важно точное количество, достаточно 1-го. Тогда триггер сработает, если при очередном опросе очереди в ней будет хотя бы 1 и более новых элементов.
* **Теги (через запятую)** — теги элементов очереди. При указании тегов триггер сработает не на все новые элементы, а только на появление элементов с указанными тегами. При этом элемент должен содержать хотя бы один из заданных тегов. 

При использовании этого триггера важно учитывать, что он работает только в связке с роботами-писателями и роботами-читателями. Поэтому интервал опроса очереди должен быть настроен так, чтобы роботы-читатели успевали считывать значения новых элементов. В противном случае триггер может срабатывать множество раз (даже бесконечно) на одни и те же новые элементы в очереди, если роботов-читателей нет, или если они не успевают читать.

### 4. Запуск при изменении папки 
Триггер срабатывает при изменении содержимого папки: добавлении/изменении/удалении файлов. Триггер бывает двух типов: для папки на машине робота или для сетевой папки. Папки должны быть настроены заранее.

Если выбрано изменение папки на машине робота, то также должна быть назначена [стратегия выполнения проектов](https://docs.primo-rpa.ru/primo-rpa/orchestrator/settings/projects-queue), разрешающая выполнение проекта на привязанных к нему роботах. Соответственно, к проекту должны быть [привязаны развернутые на данной машине роботы](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assign-task). 

Параметры триггера:

![](<../../../.gitbook/assets/триггер по изменению папки.png>) 

1. Для папки на машине робота:
   * машина робота;
   * абсолютный путь к папке.
3. Для сетевой папки:
   * [UNC-имя папки](https://learn.microsoft.com/ru-ru/dotnet/standard/io/file-path-formats#unc-paths). 
   * Шаблон фильтра папки.


### 5. Запуск при завершении проекта Роботом
Срабатывает при завершении проекта каким-либо роботом.
  
Имеет параметры:
* RPA-проект;
* результат завершения (с ошибкой или без ошибки).

### 6. Запуск из другого Робота
Срабатывает при прямом вызове триггера из робота. Имеет параметры:
* RPA-проект;
* результат завершения (с ошибкой или без ошибки)

Задание с этим триггером запускается так: 
1. Изначально выполняется задание X, в проекте которого есть элемент [Запустить робота](https://docs.primo-rpa.ru/g_elements/el_basic/els_orch/els_process/invokerobot). Этот элемент отвечает за вызов робота для другого задания (назовем его заданием Y).
2. Задание Y должно иметь триггер **Запуск из другого Робота**.
3. Как только робот начнет обрабатывать элемент **Запустить робота** в рамках задания X, произойдет запуск задания Y.
  

## Выбор нескольких триггеров

Одному заданию может быть одновременно назначено несколько триггеров. При этом триггеры работают независимо друг от друга.

![](<../../../.gitbook/assets/Триггеры.png>)

Так, на рисунке выше **Задание 1** имеет сразу 2 триггера: запуск по расписанию и запуск при получении Email. Триггер при получении Email может использоваться, например, для внепланового удаленного запуска проекта. В случае, если в определенный день, например, в выходной, отсутствует запуск по расписанию, но при этом было получено электронное письмо, то задание все равно запустится, поскольку сработал триггер **Запуск при получении Email**. 

Рассмотрим подробнее рисунок выше:
1. В процессе выполнения проекта **Задания 1** происходит запись в очередь обмена данными Queue1, на изменение которой подписано **Задание 2**.
2. В процессе выполнения проекта **Задания 2** происходит запись в папку C:\tmp на машине робота, на изменение которой подписано **Задание 3**.
3. По завершению выполнения проекта **Задания 3** запустится проект **Задания 4**, так как **Задание 4** подписано на завершение проекта **Задания 3**.

## Добавление задания

Задания создаются в разделе **Задания > Все задания** при помощи кнопки **Добавить задание**:

![](<../../../.gitbook/assets/0 (13)>)

В форме добавления заполните все необходимые поля. Если вы установили флаг **Запуск по триггеру**, потребуется выбрать тип триггера из выпадающего списка.

В случае если одному заданию назначено сразу несколько триггеров, нужно убедиться, что триггеры не вступают в логическое противоречие для RPA-проекта задания. Также проверьте, что триггеры не вступают в логическое противоречие для разных заданий.

## Управление заданиями

Задание запускается или ставится на паузу при помощи кнопок управления **Запустить/Остановить** (раздел *Все задания*). Поставить на паузу можно только задания, выполняющиеся по триггерам.

Запуск означает, что RPA-проект задания будет поставлен в очередь на выполнение. Для разового задания это произойдет сразу при запуске. Для задания по триггеру – каждый раз при срабатывании триггера. Если триггер сработал и проект помещен в очередь, то при наличии подходящего робота, проект начнет выполняться им. Если нет – проект будет находиться в очереди, пока не будет обработан или удален из неё вручную. Очередь проектов отображается в разделе главного меню [**Обзор**](https://docs.primo-rpa.ru/primo-rpa/orchestrator/monitoring/dashboard).

Чтобы изменить задание, выберите его в общем списке и нажмите кнопку **Редактировать**. Кнопка становится активной только после выбора задания.

В столбце **Состояние** выводится информация о состоянии задания - не Робота. Активных Роботов в этот момент может не быть, а проект задания может ожидать своего выполнения в очереди. Наблюдать за процессом запуска Робота можно также в разделе **Роботы > Все роботы**.\
Информация о последнем Роботе, выполняющим проект задания, отображается в столбце **История выполнения**. 

Такие общие параметры системы как *Время срабатывания задания*, *Количество роботов*, *Количество заданий* и *Количество лицензий* должны быть согласованы. Иначе возможна ситуация (при нехватке свободных роботов/лицензий) когда очередь проектов на выполнение будет только расти. Фактически это отказ в обслуживании, очередь нужно будет принудительно чистить вручную.

## Кэширование проекта

Возможно настроить кэширование проекта для более быстрого выполнения роботом. Кэширование настраивает администратор в конфигурационном файле Оркестратора. Подробности см. [здесь](https://docs.primo-rpa.ru/primo-rpa/orchestrator/fine-tuning/project-caching).
