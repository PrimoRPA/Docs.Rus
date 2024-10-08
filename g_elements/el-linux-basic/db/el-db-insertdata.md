---
Description: Insert
---

# Вставка данных

![](../../../.gitbook/assets1/studio-linux-elements-basic/insert-data-activity,.png)

Элемент производит вставку данных в указанную таблицу базы данных (БД).

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**База данных**  
*Группа свойств для установки подключения к базе данных. Заполняется в том случае, когда элемент «Вставка данных» используется вне контейнера [«Присоединиться к БД»](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_insertdata)* | |
1. **Соединение с БД\*** *[LTools.Database.DatabaseInst]* - Название переменной, хранящей инстанс соединения с БД. Используется для более быстрого подключения к уже активному соединению. Если переменная указана, то свойства «Тип БД» и «Строка соединения» заполнять не нужно.
1. **Тип БД** *[LTools.Database.Model.DatabaseTypes]* - Тип подсоединяемой базы данных. Доступные значения: <p>1. Ole DB — по умолчанию.</p> <p>2. Postgre Sql.</p> <p>3. ODBC</p> Пример: `Postgre Sql` 
1. **Строка соединения** *[String]* - Строка соединения с БД. Строку можно сформировать автоматически по кнопке <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> — в этом случае откроется окно мастера (Wizard). Пример: <p>Ole DB:</p> <p>`"Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI"`</p> <p>PostgreSQL:</p> <p> `"Host=<host>;Port=5432;Password=<password>;Username=<username>;Database=<dbname>"`</p> <p>ODBC:</p> <p>`"DRIVER=<ODBC Driver>; SERVER=<host>; PORT=<port number>;DATABASE=<dbname>; USER=<username>; PASSWORD=<password>"`</p> |

**Данные запроса** 
1. **Таблица\*** *[String]* - Название таблицы в БД, в которую вы хотите вставить данные. Пример: `"table1"`
1. **Данные\*** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0)]* - Данные в виде таблицы. Укажите название переменной.
1. **Таймаут\*** *[Int32]* - Таймаут запроса в миллисекундах. Пример: `10000`

**Вывод** 
1. **Кол-во** *[Int32]* - Итоговое количество вставленных строк.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
var connectionString = "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI";
var databaseType = LTools.Database.Model.DatabaseTypes.OleDB;

LTools.Database.DatabaseApp app = LTools.Database.DatabaseApp.Init(wf, connectionString, databaseType);

var tableName = "table";
var data = new System.Data.DataTable();
var timeout = 10000;

int res = app.Insert(tableName, data, timeout);
```
{% endtab %}

{% tab title="Python" %}
```python
connectionString = "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI";
databaseType = LTools.Database.Model.DatabaseTypes.OleDB;

app = LTools.Database.DatabaseApp.Init(wf, connectionString, databaseType)

tableName = "table";
data = new System.Data.DataTable();
timeout = 10000;

res = app.Insert(tableName, data, timeout)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var connectionString = "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI";
var databaseType = LTools.Database.Model.DatabaseTypes.OleDB;

var app = _lib.LTools.Database.DatabaseApp.Init(wf, connectionString, databaseType);

var tableName = "table";
var data = new System.Data.DataTable();
var timeout = 10000;

var res = app.Insert(tableName, data, timeout);
```
{% endtab %}
{% endtabs %}
