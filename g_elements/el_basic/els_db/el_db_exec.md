---
description: Execute query
---

# Выполнить запрос

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (246).png>)

![](<../../../.gitbook/assets/image (421).png>)

Элемент выполняет запрос к базе данных (БД). В сценарии элемент может располагаться:
* внутри контейнера [**Присоединиться к БД**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_db/el\_db\_connect);
* автономно — если другие действия с БД не предполагаются.

**Рекомендации:**

1. Если вы работаете с MS SQL, то вместо использования встроенных элементов из группы **База данных** установите nuget-пакет [Primo.Database.SqlServer](https://www.nuget.org/packages/Primo.Database.SqlServer) — в нем есть поддержка именованных аргументов для SQL-запроса (через _@Parameter_).
2. Если вы поместили запрос в контейнер **Присоединиться к БД**, то настройки соединения будут взяты из этого контейнера. Соответственно, в элементе **Выполнить запрос** такие свойства, как **Строка соединения/Соединение с БД, Тип БД** заполнять не нужно — настройки в контейнере имеют над ними приоритет.
3. Если в сценарии вы сначала используете контейнер **Присоединиться к БД**, в котором нет запросов, а сам запрос поместили ниже, вне контейнера, то в свойствах запроса вы можете применить активное подключение. Для этого сохраните в контейнере **Присоединиться к БД** активное соединение в переменную (свойство вывода **Соединение с БД**), а затем используйте эту переменную в свойстве запроса **Соединение с БД**.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство                | Тип                                                                                                          | Описание                                                                                         |
| ----------------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ |
| **База данных:**        |                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Соединение с БД         | LTools.Database.DatabaseInst                                                                                 | Инстанс соединения с БД. Заполняется, если уже имеется установленное подключение к БД, сохраненное в переменную (см. п.3 рекомендаций). При заполнении этого поля следует оставить пустыми свойства **Строка соединения** и **Тип БД**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
| Строка соединения       | String                                                                                                       | <p>Строка соединения, которая используется для установки подключения к базе данных. Вид строки зависит от выбранного типа БД и его драйвера. См. подробности для <a href="https://www.connectionstrings.com/net-framework-data-provider-for-ole-db/use-an-ole-db-provider-from-net">OLE DB</a> и <a href="https://www.connectionstrings.com/net-framework-data-provider-for-odbc/use-an-odbc-driver-from-net">ODBC</a>.<br><br>Пример для Postgre: <code>"Host=localhost;Password=1111;Username=postgres;Database=testdb"</code>. Строку можно сформировать автоматически по кнопке <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> - в этом случае откроется окно мастера (Wizard)</p> |
| Тип БД                  | -                                                                                                            | Тип подсоединяемой базы данных. Доступные значения: 1) Ole DB - **по умолчанию**; 2) Postgre Sql; 3) ODBC                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| **Данные запроса:**   |                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Текст запроса\*         | String                                                                                                       | Текст запроса SQL. Пример для Postgre: `"SELECT * FROM table1 WHERE column1 = @par1"`                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
| Аргументы (конструктор) | String                                                                                                       | <p>Аргументы запроса в строковом формате. Строку можно сформировать в окне мастера по кнопке <img src="../../../.gitbook/assets/args-constructor.png" alt="">.<br><br>Пример результата: <code>"{"Args":[{"Position":0,"Name":"@par1","Script":"\"test\""}]}"</code><br><br>Где <strong>Args</strong> - это массив аргументов. Описание аргумента массива см. в подразделе ниже</p>                                                                                                                                                                                                                                                                                                                                               |
| Аргументы (массив)      | LTools.Database.Model.ArgumentsModel                                                                         | Массив аргументов. Описание аргумента см. в подразделе ниже                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| Наличие результатов     | Boolean                                                                                                      | Признак ожидания результатов запроса - поставьте галочку, если запрос должен вернуть в ответ какие-то данные. Например, при `"SELECT * FROM table`. Если же это запрос типа `INSERT TO...` или `DELETE FROM...`, т.е. который не возвращает данные, то галочку ставить не нужно                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Таймаут                 | Int32                                                                                                        | Таймаут запроса в миллисекундах. По умолчанию 10000 мс. Верхнее значение ограничено типом данных                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| **Вывод:**         |                                                                                                              |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                   |
| Кол-во                  | Int32                                                                                                        | Количество обработанных строк                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| Переменная (массив)     | List\<List\<string>>                                                                                         | Переменная для сохранения результатов запроса в массиве                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=netcore-2.1) | Переменная для сохранения результатов запроса в Datatable                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |

## Окно мастера создания строки

Свойство **Строка соединения** имеет кнопку <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> - при ее нажатии появится мастер создания строки соединения. Окно мастера будет отличаться для разных БД — убедитесь, что свойство **Тип БД** заполнено верно.

Пример мастера для Ole DB:

![Для Ole DB](<../../../.gitbook/assets/image (301).png>)

Пример мастера для PostgreSQL:

![Для Postgre Sql](<../../../.gitbook/assets/image (383).png>)

После нажатия кнопки **OK** строка соединения будет записана в соответствующее свойство.

## Аргумент запроса

**LTools.Database.Model.ArgumentsModel** - это массив аргументов (Args).

Массив состоит из объектов **LTools.Database.Model.ArgumentsModelItem** — это аргумент запроса.\
Атрибуты:

* Position — порядковый номер аргумента. Нумерация начинается с 0 (int);
* Name — наименование аргумента (String);
* Script — значение аргумента (Object).

:bangbang: Принцип использования аргументов зависит от типа БД:

1\. Для **Ole DB** и **ODBC** в запросе вместо аргумента нужно указать знак `?`. Пример:

```
"SELECT * FROM table1 WHERE id > ?"
```

Аргумент будет вставляться в запрос вместо знака `?` соответственно заданной позиции. Атрибут имени для них не играет роли.

2\. Для **Postgre** напротив, имя аргумента важно, поскольку в запросе можно использовать именованные аргументы (через `@<parameterName>`). Пример:

```
"SELECT * FROM table1 WHERE column1 = @par1"
```

Во время выполнения команды имя аргумента будет заменено на его значение.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Database.DatabaseApp app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
List<List<string>> data = app.Execute("SELECT * FROM Table1", true);
System.Data.DataTable tbl = app.ExecuteQueryTbl("SELECT * FROM Table1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI")
data = app.Execute("SELECT * FROM Table1", True)
tbl = app.ExecuteQueryTbl("SELECT * FROM Table1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
var data = app.Execute("SELECT * FROM Table1", true);
var tbl = app.ExecuteQueryTbl("SELECT * FROM Table1");
```
{% endtab %}
{% endtabs %}

## Пример использования

Учебный пример процесса с элементом **Выполнить запрос** можно найти [здесь](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%91%D0%B0%D0%B7%D0%B0%20%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85). Процесс имеет название `Postgre.ltw`, тип процесса - **Последовательность**.
