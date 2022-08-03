# Записать в ячейку таблицы

![](<../../../../.gitbook/assets/image (561).png>)

Элемент, записывающий текст в ячейку таблицы. Элемент работает корректно только внутри контейнера Текст

| Свойство | Тип    | Описание                 |
| -------- | ------ | ------------------------ |
| Индекс   | Int32  | Порядковый номер таблицы |
| Данные   | string | Данные ячейки            |
| Строка   | Int32  | Индекс строки            |
| Колонка  | Int32  | Индекс колонки           |

{% tabs %}
{% tab title="C#" %}
```csharp
app.WriteTableCell(1, data, 2, 3);
```
{% endtab %}

{% tab title="Python" %}
```python
app.WriteTableCell(1, data, 2, 3)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.WriteTableCell(1, data, 2, 3);
```
{% endtab %}
{% endtabs %}
