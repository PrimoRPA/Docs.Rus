# Прочитать таблицу

![](<../../../../.gitbook/assets/image (506).png>)

Элемент, читающий таблицу из документа. Элемент работает корректно только внутри контейнера Текст

| Свойство | Тип                   | Описание                 |
| -------- | --------------------- | ------------------------ |
| Индекс   | Int32                 | Порядковый номер таблицы |
| Данные   | List\<List\<String>>  | Данные таблицы           |
| Таблица  | System.Data.DataTable | Данные таблицы           |

{% tabs %}
{% tab title="C#" %}
```csharp
List<List<string>> list = app.ReadTableArr(1);
System.Data.DataTable table = app.ReadTable(1);
```
{% endtab %}

{% tab title="Python" %}
```python
list = app.ReadTableArr(1) #List<List<string>>
table = app.ReadTable(1) #System.Data.DataTable
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var list = app.ReadTableArr(1); //List<List<string>>
var table = app.ReadTable(1); //System.Data.DataTable
```
{% endtab %}
{% endtabs %}
