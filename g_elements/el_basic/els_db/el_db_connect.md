# Присоединиться к БД

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (245).png>)

![](<../../../.gitbook/assets/image (330).png>)

Компонент осуществляет подключение к базе данных (БД).

| Свойство            | Тип                                 | Описание                                                                                     |
| ------------------- | ----------------------------------- | -------------------------------------------------------------------------------------------- |
| ***База данных***   |   |   |
| Строка соединения\* | String                              | Строка соединения с БД (Provider=SQLOLEDB;Data Source=\<servername>;Initial Catalog=\<dbname>;Integrated Security=SSPI). Можно заполнить по кнопке <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line">, подробности см. ниже |
| Тип БД\*            | LTools.Database.Model.DatabaseTypes | Выберите тип подсоединяемой базы данных. Доступные значения: 1) Ole DB (по умолчанию); 2) Postgre Sql; 3) ODBC |
| ***Вывод***         |   |   |
| Соединение с БД     | LTools.Database.DatabaseInst        | Инстанс соединения с БД  |


Свойство **Строка соединения** имеет кнопку <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> - при ее нажатии появится мастер создания новой строки соединения. Окно мастера будет отличаться для разных БД - убедитесь, что свойство **Тип БД** заполнено верно.

Пример мастера для Ole DB:

![Для Ole DB](<../../../.gitbook/assets/image (301).png>)

Пример мастера для PostgreSQL:

![Для Postgre Sql](<../../../.gitbook/assets/image (383).png>)

После нажатия кнопки **OK** строка соединения будет записана в соответствующее свойство.

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Database.DatabaseApp app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
```
{% endtab %}
{% endtabs %}
