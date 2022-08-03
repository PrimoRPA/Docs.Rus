# Удаление строк

![](<../../../../.gitbook/assets/image (499).png>)

Компонент, удаляющий строки из листа Таблицы.

| Свойство        | Тип    | Описание                                  |
| --------------- | ------ | ----------------------------------------- |
| Кол-во          | Int32  | Кол-во удаляемых строк                    |
| Индекс          | Int32  | Индекс строки, которую необходимо удалить |
| Страница        | String | Наименование страницы                     |
| Индекс страницы | Int32  | Индекс страницы                           |

{% tabs %}
{% tab title="C#" %}
```csharp
app.DeleteRows(2, 1, [sheet], [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.DeleteRows(2, 1, [sheet], [sheetIdx])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.DeleteRows(2, 1, [sheet], [sheetIdx]);
```
{% endtab %}
{% endtabs %}
