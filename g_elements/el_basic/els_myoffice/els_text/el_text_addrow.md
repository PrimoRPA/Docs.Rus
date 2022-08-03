# Добавить строку таблицы

![](<../../../../.gitbook/assets/image (474).png>)

Элемент, добавляющий строку к таблице. Элемент работает корректно только внутри контейнера Текст

| Свойство | Тип                 | Описание                 |
| -------- | ------------------- | ------------------------ |
| Индекс   | Int32               | Порядковый номер таблицы |
| Данные   | List\<String>       | Данные строки            |
| Строка   | System.Data.DataRow | Данные строки            |

{% tabs %}
{% tab title="C#" %}
```csharp
app.AddTableRow(1, data);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AddTableRow(1, data)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AddTableRow(1, data);
```
{% endtab %}
{% endtabs %}
