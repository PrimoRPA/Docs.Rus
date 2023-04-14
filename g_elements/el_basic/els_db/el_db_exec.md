# Выполнить запрос

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (246).png>)

![](<../../../.gitbook/assets/image (421).png>)

Компонент выполняет запрос к БД, его можно использовать:
* внутри контейнера [**Присоединиться к БД**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_connect);
* автономно - если другие действия с БД не предполагаются.

## Рекомендации

:small_blue_diamond: Если работаете с MS SQL, то вместо использования встроенных элементов из группы **База данных** установите nuget-пакет [Primo.Database.SqlServer](https://www.nuget.org/packages/Primo.Database.SqlServer) - в нем есть поддержка именованных аргументов для SQL-запроса (через *@Parameter*).

:small_blue_diamond: Если элемент используется в контейнере **Присоединиться к БД**, то значения свойств **Строка соединения/Соединение с БД, Тип БД** можно не заполнять - применятся настройки из контейнера. Они будут иметь приоритет даже в случае указания этих свойств в данном элементе.

## Свойства

Все свойства элемента разделены на группы - они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***Общие***          | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***База данных***    | |  |
| Соединение с БД      | LTools.Database.DatabaseInst | Инстанс соединения с БД. Заполняется, если уже имеется установленное подключение к БД, сохраненное в переменную. Если это поле заполнено, то свойства **Строка соединения** и **Тип БД** следует оставить пустыми |
| Строка соединения    | String                | Строка соединения, которая используется для установки подключения к базе данных. Вид строки зависит от выбранного типа БД. Пример для Postgre: `"Host=localhost;Password=1111;Username=postgres;Database=testdb"`. Строку можно сформировать автоматически по кнопке <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line">, подробности см. ниже |
| Тип БД               | -                     | Тип подсоединяемой базы данных. Доступные значения: 1) Ole DB - **по умолчанию**; 2) Postgre Sql; 3) ODBC |
| ***Данные запроса*** |  |  |
| Текст запроса\*      | String                | Текст запроса SQL. Пример для Postgre: `"SELECT * FROM table1 WHERE column1 = @par1"` |
| Аргументы (конструктор) | String             | Аргументы запроса в строковом формате. Описание аргумента см. в подразделе ниже. Пример: `"{\"Args\":[{\"Position\":0,\"Name\":\"@par1\",\"Script\":\"\\\"aaa\\\"\"}]}"` |
| Аргументы (массив)   | LTools.Database.Model.ArgumentsModel | Массив аргументов. Описание аргумента см. в подразделе ниже |
| Наличие результатов  | Boolean               | Признак ожидания результатов запроса - поставьте галочку, если запрос должен вернуть в ответ какие-то данные. Например, при `"SELECT * FROM table`. Если же это запрос типа `INSERT TO...` или `DELETE FROM...`, т.е который не возвращает данные, то галочку ставить не нужно |
| ***Вывод***          |  |  |
| Кол-во               | Int32                  | Количество обработанных строк                 |
| Переменная (массив)   | List\<List\<string>>  | Переменная для сохранения результатов запроса в массиве |
| Переменная (таблица) | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=netcore-2.1) | Переменная для сохранения результатов запроса в Datatable |

Свойство **Строка соединения** имеет кнопку <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> - при ее нажатии появится мастер создания строки соединения. Окно мастера будет отличаться для разных БД - убедитесь, что свойство **Тип БД** заполнено верно.

Пример мастера для Ole DB:

![Для Ole DB](<../../../.gitbook/assets/image (301).png>)

Пример мастера для PostgreSQL:

![Для Postgre Sql](<../../../.gitbook/assets/image (383).png>)

После нажатия кнопки **OK** строка соединения будет записана в соответствующее свойство.

## Аргумент запроса
**LTools.Database.Model.ArgumentsModelItem** - аргумент запроса.\
Атрибуты:
* Position - порядковый номер аргумента. Отсчет начинается с 0 (int);
* Name - наименование аргумента (String);
* Value - значение аргумента (Object).

:bangbang: **Важно**: PostgreSQL, в отличие от Ole DB и ODBC, поддерживает именованные аргументы, привязанные к запросу SQL. Привязка выполняется посредством указания оператора `@<parameterName>` в запросе SQL. Во время выполнения команды имя аргумента будет заменено на его значение.

## Только код

Пример использования элемента в процессе с типом **Только код (Only code)**:

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

## Учебный пример процесса
Учебный пример процесса, где используется готовый элемент **Выполнить запрос**, находится по [этой ссылке](https://github.com/PrimoRPA/Learning/tree/master/StudioActivities/Ru/%D0%91%D0%B0%D0%B7%D0%B0%20%D0%B4%D0%B0%D0%BD%D0%BD%D1%8B%D1%85). Процесс имеет название **Postgre.ltw**, тип процесса - **Последовательность**.
