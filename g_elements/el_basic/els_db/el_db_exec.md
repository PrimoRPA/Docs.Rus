# Выполнить запрос

![](<../../../.gitbook/assets/image (954).png>)

![](<../../../.gitbook/assets/image (147).png>)

Компонент, добавляющий новый элемент в коллекцию. Ожидание результатов предполагает, что запрос должен вернуть данные. Компонент корректно работает только внутри контейнера Присоединиться к БД.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| Текст запроса\*      | String                | Текст запроса SQL                             |
| Наличие результатов  | Boolean               | Признак ожидания результатов запроса          |
| Переменная(массив)   | List\<List\<string>>  | Переменная для сохранения результатов запроса |
| Переменная (таблица) | System.Data.DataTable | Переменная для сохранения результатов запроса |

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
