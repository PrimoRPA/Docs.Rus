# Добавить страницу

![](<../../../../../.gitbook/assets/image (531).png>)

Компонент, создающий новую страницу в Таблицу.

| Свойство | Тип    | Описание        |
| -------- | ------ | --------------- |
| Имя      | String | Имя страницы    |
| Индекс   | Int32  | Индекс страницы |
| Строки   | Int32  | Кол-во строк    |
| Колонки  | Int32  | Кол-во колонок  |

{% tabs %}
{% tab title="C#" %}
```csharp
app.SheetAdd("Page1", 20, 3, [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.SheetAdd("Page1", 20, 3, [sheetIdx])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SheetAdd("Page1", 20, 3, [sheetIdx]);
```
{% endtab %}
{% endtabs %}
