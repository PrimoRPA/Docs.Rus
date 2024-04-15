---
description: Execute query
---

# Выполнить запрос

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (246).png>)

![](<../../../.gitbook/assets/image (421).png>)

Элемент выполняет запрос к базе данных (БД). В сценарии элемент может использоваться:
* внутри контейнера [**Присоединиться к БД**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_db/el\_db\_connect);
* автономно — если другие действия с БД не предполагаются.

**Рекомендации:**

1. Если вы работаете с MS SQL, то вместо использования встроенных элементов из группы **База данных** установите nuget-пакет [Primo.Database.SqlServer](https://www.nuget.org/packages/Primo.Database.SqlServer) — в нем есть поддержка именованных аргументов для SQL-запроса (через _@Parameter_).
2. Если вы поместили запрос в контейнер **Присоединиться к БД**, то настройки соединения будут взяты из контейнера. Это значит, в элементе **Выполнить запрос** такие свойства, как **Строка соединения, Соединение с БД, Тип БД** заполнять не нужно — настройки в контейнере имеют приоритет.
3. Если в сценарии вы сначала используете контейнер **Присоединиться к БД**, в котором нет запросов, а сам запрос поместили ниже, вне контейнера, то в свойствах запроса возможно указать активное подключение из контейнера. Для этого сохраните в **Присоединиться к БД** установленное подключение в переменную (свойство вывода **Соединение с БД**), а затем используйте эту переменную в элементе **Выполнить запрос**, в свойстве **Соединение с БД**. 

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).
 
| Свойство                | Тип                                                                                                          | Описание                                                                                         | Пример      |
| ----------------------- | ------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------ | ----------- |
| **База данных:**        | | | |
| Соединение с БД         | LTools.Database.DatabaseInst  | Переменная, содержащая инстанс соединения с БД. Свойство заполняется, если вы хотите использовать ранее установленное и активное подключение к БД (см. п.3 рекомендаций). Если вы заполнили это свойство, оставьте пустыми свойства **Строка соединения** и **Тип БД**  |
| Строка соединения       | String   | Строка соединения, которая будет использована для установки подключения к базе данных. Вид строки зависит от выбранного типа БД и его драйвера. См. подробности для <a href="https://www.connectionstrings.com/net-framework-data-provider-for-ole-db/use-an-ole-db-provider-from-net">OLE DB</a> и <a href="https://www.connectionstrings.com/net-framework-data-provider-for-odbc/use-an-odbc-driver-from-net">ODBC</a>.<br><br>Строку можно сформировать автоматически по кнопке <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> — в этом случае откроется [окно мастера](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_exec#okno-mastera-sozdaniya-stroki) (Wizard)</p> | <p>Ole DB:</p> <p>`"Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI"`</p> <p>PostgreSQL:</p> <p> `"Host=<host>;Port=5432;Password=<password>;Username=<username>;Database=<dbname>"`</p> <p>ODBC:</p> <p>`"DRIVER=<ODBC Driver>; SERVER=<host>; PORT=<port number>;DATABASE=<dbname>; USER=<username>; PASSWORD=<password>"`</p>| 
| Тип БД                  | - | Тип базы данных. Нажмите на выпадающий список значений, чтобы выбрать доступный тип: <p>* Ole DB — по умолчанию;</p> <p>* Postgre Sql;</p> <p>* ODBC</p>  | `Postgre Sql` |
| **Данные запроса:**     | | | |
| Текст запроса\*         | String                                                                                                       | Текст запроса SQL | Postgre: <p>`"SELECT * FROM table1 WHERE column1 = @par1"`</p> |
| Аргументы (конструктор) | String                                                                                                       | <p>Аргументы запроса в строковом формате. Строку можно сформировать в окне мастера по кнопке <img src="../../../.gitbook/assets/args-constructor.png" alt="">.<br><br>Пример результата: <code>"{"Args":[{"Position":0,"Name":"@par1","Script":"\"test\""}]}"</code><br><br>Где <strong>Args</strong> — это массив аргументов. Описание аргументов массива см. в подразделе [ниже](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_exec#argument-zaprosa)</p> |
| Аргументы (массив)      | LTools.Database.Model.ArgumentsModel                                                                         | Аргументы запроса в виде массива. Описание аргументов см. в подразделе [ниже](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_exec#argument-zaprosa)   |
| Наличие результатов     | Boolean                                                                                                      | Признак ожидания результатов запроса. Поставьте галочку, если запрос должен вернуть в ответ какие-то данные. Например, вы отправили `"SELECT * FROM table` и в ответе ожидаете данные из таблицы. Если же это запрос типа `INSERT TO...` или `DELETE FROM...`, который не возвращает данные, то галочку ставить не нужно  |
| Таймаут                 | Int32                                                                                                        | Таймаут запроса в миллисекундах. Верхнее значение ограничено типом данных | `10000` |
| **Вывод:**              |  |  |  |
| Кол-во                  | Int32                                                                                                        | Количество обработанных строк   |
| Переменная (массив)     | List\<List\<string>>                                                                                         | Переменная для сохранения результатов запроса в массиве   |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=netcore-2.1) | Переменная для сохранения результатов запроса в Datatable |



## Окно мастера создания строки

:small_blue_diamond: *Для ODBC мастер отсутствует.*

Свойство **Строка соединения** имеет кнопку <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> — при ее нажатии откроется мастер создания строки соединения. Окно мастера будет отличаться для разных БД — убедитесь, что свойство **Тип БД** заполнено верно.

Пример мастера для Ole DB:

![Для Ole DB](<../../../.gitbook/assets/image (301).png>)

Пример мастера для PostgreSQL:

![Для Postgre Sql](<../../../.gitbook/assets/image (383).png>)

После нажатия кнопки **OK** строка соединения сформируется автоматически и будет записана в соответствующее свойство.

## Аргумент запроса

**LTools.Database.Model.ArgumentsModel** — это массив аргументов (Args).

Массив состоит из объектов **LTools.Database.Model.ArgumentsModelItem** — аргументов запроса.\
Атрибуты аргумента:

* Position — порядковый номер аргумента. Нумерация начинается с 0 (int).
* Name — наименование аргумента (String).
* Script — значение аргумента (Object).

:small_orange_diamond: *Принцип использования аргументов зависит от типа БД:*

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
