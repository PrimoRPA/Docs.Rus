# Отсоединиться от БД

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (65).png>)

![](<../../../.gitbook/assets/отсоединиться от бд.png>)

Элемент позволяет отсоединиться от базы данных.

| Свойство        | Тип                          | Описание                |
| --------------- | ---------------------------- | ----------------------- |
| Соединение с БД | LTools.Database.DatabaseInst | Инстанс соединения с БД |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Database.DatabaseApp app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
app.Disconnect();
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI")
app.Disconnect()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Database.DatabaseApp.Init(wf, "Provider=SQLOLEDB;Data Source=<servername>;Initial Catalog=<dbname>;Integrated Security=SSPI");
app.Disconnect();
```
{% endtab %}
{% endtabs %}
