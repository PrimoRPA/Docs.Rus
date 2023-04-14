# Выполнить запрос

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (246).png>)

![](<../../../.gitbook/assets/image (421).png>)

Компонент добавляет новый элемент в коллекцию. Ожидание результатов предполагает, что запрос должен вернуть данные. 

Компонент может работать:
* внутри контейнера [**Присоединиться к БД**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_db/el_db_connect);
* автономно - если другие действия с БД не предполагаются.

## Свойства

Все свойства элемента разделены на группы - они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***Общие***          | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***База данных***    | |  |
| Соединение с БД      | LTools.Database.DatabaseInst | Инстанс соединения с БД                |
| Строка соединения    | String                | Строка соединения с БД                        |
| Тип БД               | -                     | Тип подсоединяемой базы данных. **Важно: если элемент используется в контейнере, значение свойства игнорируется - тип БД определяется настройками в контейнере** |
| ***Данные запроса*** |  |  |
| Текст запроса\*      | String                | Текст запроса SQL                             |
| Аргументы (конструктор) | String             | Аргументы запроса                             |
| Аргументы (массив)   | LTools.Database.Model.ArgumentsModel | Массив аргументов. Параметры аргумента описаны ниже |
| Наличие результатов  | Boolean               | Признак ожидания результатов запроса          |
| ***Вывод***          |  |  |
| Кол-во               | Int32                 | Количество обработанных строк                 |
| Переменная(массив)   | List\<List\<string>>  | Переменная для сохранения результатов запроса |
| Переменная (таблица) | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=netcore-2.1) | Переменная для сохранения результатов запроса |

**LTools.Database.Model.ArgumentsModelItem** - аргумент запроса из массива.\
Параметры:
* Position - порядковый номер (int);
* Name - наименование (String);
* Value - значение (Object).

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
