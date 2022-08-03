# Вставить таблицу

![](<../../../../.gitbook/assets/image (552).png>)

Элемент, вставляющий таблицу в документ. Элемент работает корректно только внутри контейнера Текст

| Свойство | Тип                   | Описание                                                                                      |
| -------- | --------------------- | --------------------------------------------------------------------------------------------- |
| Закладка | String                | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Данные   | List\<List\<String>>  | Данные таблицы                                                                                |
| Таблица  | System.Data.DataTable | Данные таблицы                                                                                |

{% tabs %}
{% tab title="C#" %}
```csharp
app.InsertTable(data, [bookmark]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.InsertTable(data, [bookmark])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.InsertTable(data, [bookmark]);
```
{% endtab %}
{% endtabs %}
