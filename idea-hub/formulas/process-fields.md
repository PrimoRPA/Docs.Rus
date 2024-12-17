# Поля и методы процесса

## Название

**Тип поля**: Текст (простой)

**Машинное имя**: title

**Описание**: Нет описания

## Ключ для расчёта

**Тип поля**: Текст (простой)

**Машинное имя**: key

**Описание**: Ключ используется для доступа к свойствам сущности в формулах.

## Описание

**Тип поля**: Текст (форматированный, длинный, с резюме)

**Машинное имя**: body

**Описание**: Нет описания

## Департамент

**Тип поля**: Entity reference

**Машинное имя**: field_area

**Описание**: Ссылка на элемент управления, которому принадлежит процесс.

## Автоматизация

**Тип поля**: Число (десятичное)

**Машинное имя**: field_automation_prc

**Описание**: Потенциальный процент автоматизации бизнес-процессов.

## Фактический процент автоматизации

**Тип поля**: Формула

**Машинное имя**: field_automation_prc_real

**Описание**: Нет описания

**Формула**

```
vars:
  total: |
    this.field_ops_total == 0 ? null : this.field_ops_total
  zero: this.field_ops_total - this.field_ops_exception
  result: |
    total == null ? total : zero == 0 ? 0 : (this.field_ops_success / (this.field_ops_total - this.field_ops_exception)) * 100
exp: result
```

## Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: avg(this.field('field_automation_prc_real'))
  delta: value - this.field_automation_prc
exp: |
  {"value": value, "delta": delta}
```

## Аналитик

**Тип поля**: Entity reference

**Машинное имя**: field_ba

**Описание**: Ответственный аналитик.

## Сложность

**Тип поля**: Entity reference

**Машинное имя**: field_complexity

**Описание**: Ожидаемые трудности в автоматизации бизнес-процесса.

## Контакты

**Тип поля**: Entity reference

**Машинное имя**: field_contacts

**Описание**: Сотрудники, владеющие информацией о процессе.

#### Разработчик

**Тип поля**: Entity reference

**Машинное имя**: field_dev

**Описание**: Нет описания

#### Стоимость разработки

**Тип поля**: Число (дробное)

**Машинное имя**: field_dev_cost

**Описание**: Нет описания

#### Дата начала разработки

**Тип поля**: Дата

**Машинное имя**: field_dev_started

**Описание**: Нет описания

#### Фактическая утилизация лицензии робота

**Тип поля**: Формула

**Машинное имя**: field_disposal_licenses

**Описание**: Число лицензий использованных процессом за день.

**Формула**

```
(this.field_ops_total * this.field_ops_duration_avg) / 60 / 1440
```

#### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: avg(this.field('field_disposal_licenses')) * 100 * 30 / 30
  delta: (value - this.field_disposal_licenses_expected * 100 * 30 / 30)
exp: |
  {"value": value, "delta": delta}

```

#### Отображение teaser
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  orch: this.comp_orch_connected
  value: | 
    orch ? (avg(this.field('field_disposal_licenses')) * 30) : (this.field_disposal_licenses_expected * 30)
exp: |
  {"value": value}
```

## Плановая утилизация лицензии робота

**Тип поля**: Формула

**Машинное имя**: field_disposal_licenses_expected

**Описание**: Нет описания

**Формула**

```
(this.field_ops_pd_expected * this.field_human_duration) / 1440 / 3
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
{"value": this.field_disposal_licenses_expected * 100}
```

## Документация

**Тип поля**: Файл

**Машинное имя**: field_docs

**Описание**: Нет описания

## Длительность (deprecated)

**Тип поля**: Число (десятичное)

**Машинное имя**: field_duration

**Описание**: Средняя продолжительность одной операции в минутах.

## Контур

**Тип поля**: Entity reference

**Машинное имя**: field_environment

**Описание**: Внутренний контур организации, в котором выполняется процесс.

## Фактический FTE

**Тип поля**: Формула

**Машинное имя**: field_fte

**Описание**: Количество человеческого труда требуемого для реализации процесса в текущий день, без автоматизации.

**Формула**

```
(this.field_ops_success * this.field_human_duration) / WORK_MONTH_MINUTES
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: avg(this.field('field_fte')) * 30
  delta: value - this.field_fte_savings
exp: |
  {"value": value, "delta": delta}
```

### Отображение teaser
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  orch: this.comp_orch_connected
  prev: this.field_fte_savings
  value: | 
    orch ? (avg(this.field('field_fte')) * 30) : this.field_fte_savings
  delta: | 
    orch ? value - prev : null
exp: |
  {"value": value, "delta": delta}
```

## Неавтоматизируeмый человеческий труд

**Тип поля**: Формула

**Машинное имя**: field_fte_after

**Описание**: Количество человеческого труда, которое необходимо для реализации данного процесса с учётом автоматизации.

**Формула**

```
((this.field_ops_error + this.field_ops_exception) * this.field_human_duration) / WORK_MONTH_MINUTES
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
{"value": avg(this.field('field_fte_after')) * 30}
```

### Отображение teaser
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  orch: this.comp_orch_connected
  value: | 
    orch ? (avg(this.field('field_fte_after')) * 30) : this.field_fte_savings * (100 - this.field_automation_prc) / 100
exp: |
  {"value": value}
```

## Стоимость FTE

**Тип поля**: Число (десятичное)

**Машинное имя**: field_fte_human_fte_cost

**Описание**: Стоимость рабочего месяца человека, выполняющего данный процесс.

## Плановый FTE

**Тип поля**: Формула

**Машинное имя**: field_fte_savings

**Описание**: Величина сокращения FTE за счёт применения робота, с учётом ошибок автоматизации и процента автоматизации. Другими словами, количество человеческого труда, которое нам больше не понадобится.

**Формула**

```
((this.field_ops_pd_expected * this.field_human_duration) / WORK_DAY_MINUTES) * (this.field_automation_prc / 100)
```

### Отображение teaser
**Тип**: delta_formatter

**Настройки**: 
```
{"value": this.field_fte_savings}
```

## Экономия Ручного Труда в FTE

**Тип поля**: Формула

**Машинное имя**: field_ftes

**Описание**: Предполагаемая экономия FTE после автоматизации. Это то, что ожидалось на этапе планирования роботизации.

**Формула**

```
((this.field_ops_success * this.field_human_duration) / WORK_DAY_MINUTES) * (this.field_automation_prc / 100)
```

## Длительность (ручная)

**Тип поля**: Число (десятичное)

**Машинное имя**: field_human_duration

**Описание**: Длительность транзакции при выполнении человеком (в минутах).

## ID процесса

**Тип поля**: Текст (простой)

**Машинное имя**: field_id

**Описание**: Уникальный идентификатор процесса

## Тип лицензии

**Тип поля**: Entity reference

**Машинное имя**: field_license_type

**Описание**: Нет описания

## Машины

**Тип поля**: Entity reference

**Машинное имя**: field_machine

**Описание**: Машины, на которых работают роботы.

## Средняя длительность

**Тип поля**: Формула

**Машинное имя**: field_ops_duration_avg

**Описание**: Average element process duration in seconds.

**Формула**

```
this.stat('duration_avg')
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: round(avg(this.field('field_ops_duration_avg')) / 60)
  delta: value - this.human_duration
exp: |
  {"value": value, "delta": delta}
```

## Ошибка

**Тип поля**: Формула

**Машинное имя**: field_ops_error

**Описание**: Amount of business exceptions.

**Формула**

```
this.stat('error')
```

## Исключения

**Тип поля**: Формула

**Машинное имя**: field_ops_exception

**Описание**: Number of business exceptions.

**Формула**

```
this.stat('exception')
```

## Период операций

**Тип поля**: Список (текст)

**Машинное имя**: field_ops_period

**Описание**: Период, за который указано значение в поле "Количество операций".

## Успешно

**Тип поля**: Формула

**Машинное имя**: field_ops_success

**Описание**: Number of successfully processed elements.

**Формула**

```
this.stat('success')
```

## Всего

**Тип поля**: Формула

**Машинное имя**: field_ops_total

**Описание**: The total number of business elements process attempts.

**Формула**

```
this.stat('total')
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: avg(this.field('field_ops_total')) * 30
  delta: value - this.field_transactions
exp: |
  {"value": value, "delta": delta}
```

## Проекты

**Тип поля**: Entity reference

**Машинное имя**: field_orch_project

**Описание**: Проекты, связанные с процессами и выполняемые в оркестраторе.

## Идентификаторы проектов

**Тип поля**: Текст (простой)

**Машинное имя**: field_orch_project_ids

**Описание**: Поле содержит идентификаторы проектов в том виде, в каком они записаны в файле обмена данными. Это поле не должно быть редактируемым. Система автоматически управляет значениями этого поля.

## Названия проектов

**Тип поля**: Текст (простой, длинный)

**Машинное имя**: field_orch_project_names

**Описание**: Поле содержит названия или части названий проектов так, как они записаны в файле обмена данными. Это поле не должно быть редактируемым. Система автоматически управляет значениями этого поля.

## Владелец процесса

**Тип поля**: Entity reference

**Машинное имя**: field_owner

**Описание**: Нет описания

## Дата выпуска промышленного решения

**Тип поля**: Текст (простой)

**Машинное имя**: field_planned_release_date

**Описание**: Planned release date for the industrial solution

## Планы по целевой автоматизации

**Тип поля**: Текст (простой, длинный)

**Машинное имя**: field_plans

**Описание**: Нет описания

## Дата начала

**Тип поля**: Дата

**Машинное имя**: field_production_since

**Описание**: Дата ввода в эксплуатацию (используется для расчета эффектов).

## Вывод процесса из эксплуатации

**Тип поля**: Дата

**Машинное имя**: field_production_until

**Описание**: Дата планового вывода процесса из эксплуатации.

## Очередь

**Тип поля**: Entity reference

**Машинное имя**: field_queue

**Описание**: Вы можете связать с данным процессом несколько очередей, однако данные для расчётов будут браться только из первой очереди из списка. Для изменения порядка следования очередей в списке, вы можете перемещать их с помощью перетаскивания.

## Плановый эффект, в месяц

**Тип поля**: Формула

**Машинное имя**: field_revenue_expected

**Описание**: Нет описания

**Формула**

```
this.field_fte_savings * this.field_fte_human_fte_cost * SALARY_INCREASE_FACTOR
```

## Фактический эффект

**Тип поля**: Формула

**Машинное имя**: field_revenue_real

**Описание**: Эффект в деньгах.

**Формула**

```
this.field_fte * this.field_fte_human_fte_cost * SALARY_INCREASE_FACTOR
```

### Отображение default
**Тип**: delta_formatter

**Настройки**: 
```
vars:
  value: avg(this.field('field_revenue_real', null, 'last day of previous month', 'month', 'sum'))
  delta:  value - this.field_revenue_expected
exp: |
  {"value": value, "delta": delta} 
```

## Revision date

**Тип поля**: Дата

**Машинное имя**: field_revision_date

**Описание**: The date of current revision. Entity store historical stat and calculated data for this date.

## роботов

**Тип поля**: Entity reference

**Машинное имя**: field_robot

**Описание**: Роботы, на которых можно выполнить процесс.

## Пользователь робота

**Тип поля**: Entity reference

**Машинное имя**: field_robot_user

**Описание**: Нет описания

## Источник статистики

**Тип поля**: Список (текст)

**Машинное имя**: field_rpa_stat_source

**Описание**: Источник статистики операций RPA

## Экономический эффект

**Тип поля**: Формула

**Машинное имя**: field_savings

**Описание**: Расчет прямого экономического эффекта от применения автоматизации.

**Формула**

```

```

## Расписание

**Тип поля**: Entity reference

**Машинное имя**: field_schedule

**Описание**: Доступные интервалы запуска.

## Системы

**Тип поля**: Entity reference

**Машинное имя**: field_systems

**Описание**: Затронутые системы.

## Теги

**Тип поля**: Entity reference

**Машинное имя**: field_tags

**Описание**: Используйте теги, чтобы группировать процессы по схожим темам и категориям.

## Тенант

**Тип поля**: Entity reference

**Машинное имя**: field_tenant

**Описание**: Нет описания

## Количество операций

**Тип поля**: Число (десятичное)

**Машинное имя**: field_transactions

**Описание**: Количество операций, совершенных за период, указанный в поле "Период операций".

## Тип автоматизации

**Тип поля**: Entity reference

**Машинное имя**: field_type

**Описание**: Основной вид автоматизации бизнес-процессов.

## Статус

**Тип поля**: Статус

**Машинное имя**: field_workflow

**Описание**: Статус жизненного цикла.

## Средняя продолжительность одной операции

**Тип поля**: Число (дробное)

**Машинное имя**: field_duration_computed

**Описание**: Средняя продолжительность одной операции в минутах.

## Всего выполнено операций

**Тип поля**: Формула

**Машинное имя**: field_ops_total_second

**Описание**: Нет описания

**Формула**

```
Нет значения по умолчанию
```

## Количество дней в разработке

**Тип поля**: Число (целое)

**Машинное имя**: time_in_dev

**Описание**: Подсчитывает количество дней, в течение которых процесс находится (находился) в разработке.

## Количество дней в эксплуатации

**Тип поля**: Число (целое)

**Машинное имя**: comp_prod_num_days

**Описание**: The estimated number of days the process will run in production.

## Оркестратор подключен

**Тип поля**: Логическое

**Машинное имя**: comp_orch_connected

**Описание**: Указывает, подключен ли этот процесс к оркестратору или нет.

## Ожидаемых операций в день

**Тип поля**: Число (дробное)

**Машинное имя**: field_ops_pd_expected

**Описание**: Calculates the frequency of business operations per day using either data entered by the user or data received from the Orchestrator. Priority is given to data received from the Orchestrator.


# Методы процесса



**Метод:** `stat`

**Описание:** Get the statistics of a given process for a selected date.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date** (string|null): The date for which you need to obtain statistics. By default, this is
the current date.



**Пример**

* `this.stat('success') // Вернёт количество успешных запусков за последнюю доступную дату.`
* `this.stat('total') // Вернёт количество запусков всего за последнюю доступную дату.`
* `this.stat('total', '2024-10-12') // Вернёт количество запусков всего за 12 октября 2024 года.`

---

**Метод:** `field`

**Описание:** Get the range of field value. Can be groupped and aggregated.

**Параметры:**

* **field_name** (string): The name of the field of a given entity.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.
* **group_name** (string|null): The name of the group of date. Possible values:
  - week;
  - month;
  - quarter;
  - year.
* **aggregator_name** (string|null): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.



**Пример**

* `this.field('field_ops_success')`
* `this.field('field_revenue_expected', '1/1 this year', 'now', 'month', 'avg')`
* `this.field('field_ops_success', '1/1 this year', 'now', 'month', 'sum')`

---

**Метод:** `stat_range`

**Описание:** Get the range of statistics values for a given process.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range('success', '2024-01-01', '2024-12-31')`

---

**Метод:** `stat_agg`

**Описание:** Get aggregated statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_agg('success', 'sum')`
* `this.stat_agg('success', 'sum', '2024-01-01', '2024-12-31')`
* `this.stat_agg('total', '-2 quarter first day', '-2 quarter last day')`

---

**Метод:** `stat_range_agg`

**Описание:** Get aggregated and groupped statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **group** (string): The name of the group of date. Possible values:
  - week;
  - month;
  - quarter;
  - year.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range_agg('success', 'avg', 'month')`
* `this.stat_range_agg('success', 'avg', 'month', '2024-01-01', '2024-06-06')`

---



# Методы проекта



**Метод:** `stat`

**Описание:** Get the statistics of a given process for a selected date.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date** (string|null): The date for which you need to obtain statistics. By default, this is
the current date.



**Пример**

* `this.stat('success')`
* `this.stat('total')`

---

**Метод:** `stat_range`

**Описание:** Get the range of statistics values for a given process.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range('success', '2024-01-01', '2024-12-31')`

---

**Метод:** `stat_agg`

**Описание:** Get aggregated statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_agg('success', 'sum')`
* `this.stat_agg('success', 'sum', '2024-01-01', '2024-12-31')`
* `this.stat_agg('total', '-2 quarter first day', '-2 quarter last day')`

---

**Метод:** `stat_range_agg`

**Описание:** Get aggregated and groupped statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **group** (string): The name of the group of date. Possible values:
  - week;
  - month;
  - quarter;
  - year.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range_agg('success', 'avg', 'month')`
* `this.stat_range_agg('success', 'avg', 'month', '2024-01-01', '2024-06-06')`

---



# Методы очереди



**Метод:** `stat`

**Описание:** Get the statistics of a given process for a selected date.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date** (string|null): The date for which you need to obtain statistics. By default, this is
the current date.



**Пример**

* `this.stat('success')`
* `this.stat('total')`

---

**Метод:** `stat_range`

**Описание:** Get the range of statistics values for a given process.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range('success', '2024-01-01', '2024-12-31')`

---

**Метод:** `stat_agg`

**Описание:** Get aggregated statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_agg('success', 'sum')`
* `this.stat_agg('success', 'sum', '2024-01-01', '2024-12-31')`
* `this.stat_agg('total', '-2 quarter first day', '-2 quarter last day')`

---

**Метод:** `stat_range_agg`

**Описание:** Get aggregated and groupped statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **group** (string): The name of the group of date. Possible values:
  - week;
  - month;
  - quarter;
  - year.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range_agg('success', 'avg', 'month')`
* `this.stat_range_agg('success', 'avg', 'month', '2024-01-01', '2024-06-06')`

---



# Методы робота



**Метод:** `stat`

**Описание:** Get the statistics of a given process for a selected date.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date** (string|null): The date for which you need to obtain statistics. By default, this is
the current date.



**Пример**

* `this.stat('success')`
* `this.stat('total')`

---

**Метод:** `stat_range`

**Описание:** Get the range of statistics values for a given process.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range('success', '2024-01-01', '2024-12-31')`

---

**Метод:** `stat_agg`

**Описание:** Get aggregated statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_agg('success', 'sum')`
* `this.stat_agg('success', 'sum', '2024-01-01', '2024-12-31')`
* `this.stat_agg('total', '-2 quarter first day', '-2 quarter last day')`

---

**Метод:** `stat_range_agg`

**Описание:** Get aggregated and groupped statistics for a specified period.

**Параметры:**

* **ops_name** (string): Title of the statistic. Possible values:
  - total;
  - success;
  - error;
  - exception;
  - duration_avg.
* **agg_name** (string): The name of the aggregating function. Possible values:
  - sum;
  - avg;
  - med;
  - last.
* **group** (string): The name of the group of date. Possible values:
  - week;
  - month;
  - quarter;
  - year.
* **date_start** (string|null): Range start date. By default, this is the Commissioning date from
field_production_since field of the proccess entity value.
* **date_end** (string|null): Range end date. By default, this is the date of planned or actual process
decommissioning from field_production_until field of the proccess entity
value.



**Пример**

* `this.stat_range_agg('success', 'avg', 'month')`
* `this.stat_range_agg('success', 'avg', 'month', '2024-01-01', '2024-06-06')`

---
