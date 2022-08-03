# Ввод в ячейку

![](<../../../../.gitbook/assets/image (503).png>)

Компонент, производящий запись данных в ячейку Таблицы.

| Свойство        | Тип     | Описание                      |
| --------------- | ------- | ----------------------------- |
| Страница        | String  | Наименование страницы         |
| Индекс страницы | Int32   | Индекс страницы               |
| Как текст       | Boolean | Вставлять значение, как текст |
| Числовой формат | String  | Формат вводимого числа (#,#)  |
| Данные          | String  | Данные, вводимые в ячейку     |
| Ячейка          | String  | Идентификатор ячейки (A4)     |

{% tabs %}
{% tab title="C#" %}
```csharp
app.WriteCell("A4", "Value", [sheet], [sheetIdx], [numFormat]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.WriteCell("A4", "Value", [sheet], [sheetIdx], [numFormat])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.WriteCell("A4", "Value", [sheet], [sheetIdx], [numFormat]);
```
{% endtab %}
{% endtabs %}
