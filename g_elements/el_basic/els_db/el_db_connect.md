# Присоединиться к БД

![](<../../../.gitbook/assets/image (6).png>)

![](<../../../.gitbook/assets/image (330).png>)

Компонент, осуществляющий подключение к базе данных.

| Свойство            | Тип                                 | Описание                                                                                                                |
| ------------------- | ----------------------------------- | ----------------------------------------------------------------------------------------------------------------------- |
| Строка соединения\* | String                              | Строка соединения с БД (Provider=SQLOLEDB;Data Source=\<servername>;Initial Catalog=\<dbname>;Integrated Security=SSPI) |
| Тип БД\*            | LTools.Database.ModelюDatabaseTypes | Тип подсоединяемой Базы Данных                                                                                          |

При нажатии кнопки "Строка соединения" <img src="../../../.gitbook/assets/connection_editor_button.png" alt="" data-size="line"> появится мастер создания новой строки соединения

![Для Ole DB](<../../../.gitbook/assets/image (301).png>)

![Для Postgre Sql](<../../../.gitbook/assets/image (383).png>)

После нажатия кнопки OK, строка соединения будет записана в соответствующее свойство

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
