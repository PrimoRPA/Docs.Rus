# Синтаксис формул

## Поддерживаемые литералы

* **строки** - одинарные и двойные кавычки (например ``'hello'``)
* **числа** - целое число (e.g. ``103``), десятичная дробь (e.g. ``9.95``), десятичные дроби
  без ведущих нулей (например ``.99``, эквивалентно ``0.99``); все числа
  поддерживают дополнительные подчеркивания в качестве разделителей для улучшения читаемости (например
  ``1_000_000``, ``3.14159_26535``)
* **массивы** - используя нотацию типа JSON (e.g. ``[1, 2]``)
* **именованные массивы** - используя нотацию типа JSON (e.g. ``{ foo: 'bar' }``)
* **логические значения** - ``true`` и ``false``
* **нулевой** - ``null``
* **экспоненциальный** - также известный как научный (например ``1.99E+3`` или ``1e-2``)

## Null-Coalescing Operator

Он возвращает левую часть, если она существует и не равна ``null``; иначе возвращает правую часть. Выражения могут объединять несколько операторов объединения:

* ``foo ?? 'no'``
* ``foo.baz ?? 'no'``
* ``foo[3] ?? 'no'``
* ``foo.baz ?? foo['baz'] ?? 'no'``

## Поддерживаемые операторы

### Арифметические операторы

* ``+`` (сложение)
* ``-`` (вычитание)
* ``*`` (умножение)
* ``/`` (деление)
* ``%`` (модуль)
* ``**`` (возведение в степень)

### Побитовые операторы

* ``&`` (и)
* ``|`` (или)
* ``^`` (исключающее или)

### Comparison Operators

* ``==`` (равно)
* ``===`` (идентично)
* ``!=`` (не равно)
* ``!==`` (не идентично)
* ``<`` (меньше чем)
* ``>`` (больше чем)
* ``<=`` (меньше или равно)
* ``>=`` (больше или равно)
* ``matches`` (совпадение с регулярным выражением)
* ``contains`` (содержит)
* ``starts with`` (начинается с)
* ``ends with`` (заканчивается на)

Чтобы проверить, что строка **не** соответствует регулярному выражению, используйте логический оператор ``not`` в комбинации с оператором ``matches``:

```
not ("foo" matches "/bar/") // вернёт true
```

Вы должны использовать круглые скобки, поскольку унарный оператор ``not`` имеет приоритет над бинарным оператором ``matches``.

### Логические операторы
* ``not`` или ``!``
* ``and`` или ``&&``
* ``or`` или ``||``

### String Operators
``~`` (конкатенация)

Пример использования:

```
"Hello" ~ " World!" // вернёт "Hello World!"
```

### Операторы массивов

* ``in`` (содержит)
* ``not in`` (не содержит)

Например:

``` 
'one' in ['one', 'two'] ? 'true' : 'false' // вернёт true
```

## Переменные

Вы можете использовать в выражениях переменные. Есть два варианта определения и использования переменных.

Переменные это текст с завершающим символом ":", после которого следует некоторое выражение. Например:

```
one: 1
two: one + 1

one + two
```
По шагам:
1. В первой строке, определяется переменная ``one`` со значением 1.
1. Во второй строке, определяется переменная ``two``, значение которой это выражение.
1. Третья строка, это результирующее выражение, которое и будет результатом вычисления.

## Данные

В Idea Hub доступны следующие данные:

* **process** (процессы)
* **license** (лицензии)
* **robot** (роботы)
* **machine** (машины)
* **queue** (очереди)
* **project** (проекты)
* **areas** (департаменты)
* **process_type** (типы процессов)
* **tenant** (тенанты)
* **systems** (системы)
* **environment** (окружения)
* **license_type** (типы лицензий)
* **process_complexity** (уровни сложности процессов)
* **folder** (папки)

С помощью этих ключевых слов, можно получить доступ к списку соответствующих данных.

### Примеры использования данных

```
process.list()
```

Результатом вычисления будет именованный массив всех процессов в системе.

```
{
    "process#14541": {},
    "process#14542": {},
    "process#14543": {}
}
```

### Доступ к полям

Чтобы посмотреть список доступных полей сущности, вам нужно в редакторе формул написать выражение:

```
?> fields process 
```

Это выражение может быть размещено в конце любого другого выражения на отдельной последней строке. В таком случае, 
подсказку по списку полей вы увидите в одной части панели с результатами расчётов, а результат вычисления в другой части. 

Следующее выражение будет корректным:

```
process#14545.field_duration
?> fields process длительность
```

Результатом выполнения первой строки выражения будет число 6.

Результатом выполнения второй строки выражения, будет следующее:

```
{
    "field_duration": {
        "псевдоним": "duration",
        "name": "Длительность (deprecated)",
        "description": "Средняя продолжительность одной операции в минутах."
    },
    "field_human_duration": {
        "псевдоним": "human_duration",
        "name": "Длительность (ручная)",
        "description": "Длительность транзакции при выполнении человеком (в минутах)."
    },
    "field_ops_duration_avg": {
        "псевдоним": "ops_duration_avg",
        "name": "Средняя длительность",
        "description": ""
    }
}
```

Справа на панели, появится текст со списком доступных полей для процессов. Чтобы найти среди полей нужное, вы можете продолжить ввод. Весь дальнейший текст ввода будет использоваться в качестве шаблона для поиска полей. Поиск ведётся по названию поля и описанию. 

Пример:

```
?> fields process разраб
```

Покажет вам список полей, в описании или названии которых встречается слово "разраб":

```
{
    "field_dev": {
        "псевдоним": "dev",
        "name": "Разработчик",
        "description": ""
    },
    "field_dev_cost": {
        "псевдоним": "dev_cost",
        "name": "Стоимость разработки",
        "description": ""
    },
    "field_dev_started": {
        "псевдоним": "dev_started",
        "name": "Дата начала разработки",
        "description": ""
    },
    "time_in_dev": {
        "name": "Количество дней в разработке",
        "description": "Подсчитывает количество дней, в течение которых процесс находится (находился) в разработке."
    }
}
```

Выражение ``process#14541`` используется для доступа к конкретному процессу. Например:

```
process#14541.field_fte
```
Вернёт вычисленное значение поля ``field_fte`` (FTE) на текущую дату.

А следующее выражение:
```
process#14541.field('field_fte', '2024-05-12')
```

Вернёт значение поля ``field_fte`` на 12 мая 2024 года.



## Функции

###  count(array) 
Количество элементов массива.

* **Аргументы:** array - массив.
* **Пример:** ``count([1, 2, 3])`` вернёт 3.

### sum(array) 
Сумма элементов массива.

* **Аргументы:** array - массив, значения которого будут просуммированы.
* **Пример:** ``sum([1, 2, 3])`` вернёт 6.

### avg(array) 
Среднее всех элементов массива.

* **Аргументы:** array - массив, значения которого будут использованы для вычисления среднего значения.
* **Пример:** ``avg([1, 2, 3])`` вернёт 2.

Если в массиве присутствуют пустые значения, они будут исключены из вычисления.

Например:

```
avg([1, 2, null, 3])
```

Также вернёт 2, потому что элемент со значением ``null`` не будет учитываться во время вычисления.