# Удаление колонок

![](<../../../../.gitbook/assets/image (515).png>)

Компонент, удаляющий колонки из листа Таблицы.

| Свойство        | Тип    | Описание                                   |
| --------------- | ------ | ------------------------------------------ |
| Кол-во          | Int32  | Кол-во удаляемых колонок                   |
| Индекс          | Int32  | Индекс колонки, которую необходимо удалить |
| Страница        | String | Наименование страницы                      |
| Индекс страницы | Int32  | Индекс страницы                            |

{% tabs %}
{% tab title="C#" %}
```csharp
app.DeleteColumns(2, 1, [sheet], [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.DeleteColumns(2, 1, [sheet], [sheetIdx])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.DeleteColumns(2, 1, [sheet], [sheetIdx]);
```
{% endtab %}
{% endtabs %}
