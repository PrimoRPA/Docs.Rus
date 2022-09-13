# Вставить таблицу

![](<../../../.gitbook/assets/image (528).png>)



Компонент, производящий вставку таблицы в презентацию.

Свойства

| Свойство               | Тип                                          | Описание                         |
| ---------------------- | -------------------------------------------- | -------------------------------- |
| Индекс слайда          | Int32                                        | Индекс слайда                    |
| Фигура                 | String                                       | Имя фигуры для вставки           |
| Таблица                | System.Data.DataTable                        | Таблица данных для вставки       |
| Исключить заголовки    | Boolean                                      | Не включать заголовки в таблицу  |
| Режим                  | Primo.Office.PowerPoint. Model.AddTableTypes | Режим вставки данных             |
| Перезаписать со строки | Int32                                        | Перезаписывать начиная со строки |
| Перезаписать с колонки | Int32                                        | Перезаписывать начиная с колонки |

{% tabs %}
{% tab title="C#" %}
```csharp
app.AddDataTable(1, "Shape1", tbl, true, Primo.Office.PowerPoint.Model.AddTableTypes.CreateNewTable, 2, 3);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AddDataTable(1, "Shape1", tbl, True, Primo.Office.PowerPoint.Model.AddTableTypes.CreateNewTable, 2, 3)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AddDataTable(1, "Shape1", tbl, true, _lib.Primo.Office.PowerPoint.Model.AddTableTypes.CreateNewTable, 2, 3);
```
{% endtab %}
{% endtabs %}
