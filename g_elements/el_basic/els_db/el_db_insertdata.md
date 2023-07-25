# Вставка данных

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (65).png>)

![](<../../../.gitbook/assets/бд. вставка данных.png>)

Позволяет вставить данные в таблицу базы данных.

| Свойство          | Тип                                                                                                      | Описание                                                                                                     |
| ----------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| Соединение с БД\* | LTools.Database.DatabaseInst                                                                             | Инстанс соединения с БД                                                                                      |
| Тип БД            | LTools.Database.Model.DatabaseTypes                                                                      | Тип подсоединяемой базы данных                                                                               |
| Строка соединения | String                                                                                                   | Строка соединения с БД. Например: "Provider=SQLOLEDB;Data Source=;Initial Catalog=;Integrated Security=SSPI" |
| Таблица\*         | String                                                                                                   | Название таблицы в БД, в которую нужно вставить данные                                                       |
| Данные\*          | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0) | Данные в виде таблицы                                                                                        |
| Таймаут\*         | Int32                                                                                                    | Таймаут запроса                                                                                              |
| Кол-во            | Int32                                                                                                    | Количество вставленных строк                                                                                 |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Database.DatabaseApp app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
int res = app.Insert("table", data);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI")
res = app.Insert("table", da
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI"); 
var res = app.Insert("table", data);
```
{% endtab %}
{% endtabs %}
