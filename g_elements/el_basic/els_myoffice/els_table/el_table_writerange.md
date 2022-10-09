# Запись диапазона

![](<../../../../.gitbook/assets/image (839).png>)

Компонент, записывающий данные диапазона ячеек в Таблицу.

| Свойство                | Тип                                                                                            | Описание                                                 |
| ----------------------- | ---------------------------------------------------------------------------------------------- | -------------------------------------------------------- |
| Диапазон                | String                                                                                         | Диапазон записи ячеек (A1:D12)                           |
| Добавлять заголовки     | Boolean                                                                                        | Добавлять заголовки колонок таблицы                      |
| Страница                | String                                                                                         | Наименование страницы                                    |
| Индекс страницы         | Int32                                                                                          | Индекс страницы                                          |
| Как текст               | Boolean                                                                                        | Вставлять значение, как текст                            |
| Числовой формат         | String                                                                                         | Формат вводимого числа (#,#)                             |
| Перезаписать            | Boolean                                                                                        | Признак перезаписи данных                                |
| Направление             | LTools.Office.Model. ExcelRangeMoveDirections                                                  | Направление сдвига ячеек                                 |
| Расширять диапазон      | Boolean                                                                                        | Автоматически расширять диапазон до размеров данных      |
| Переменная (текст)      | List\<List\<String>>                                                                           | Переменная для хранения данных записи текстовых значений |
| Переменная (таблица)    | System.Data.DataTable                                                                          | Переменная для хранения данных текстовых значений        |
| Переменная (информация) | List\<List<[LTools.Office. Model.ExcelCellInfo](../../els\_excel/datatypes/excelcellinfo.md)>> | Переменная для хранения данных информации о ячейках      |

{% tabs %}
{% tab title="C#" %}
```csharp
app.AppendRange(data, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat]);
app.AppendRange(data_info, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat]);
app.AppendRange(dataTable, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat]);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AppendRange(data, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat])
app.AppendRange(data_info, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat])
app.AppendRange(dataTable, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AppendRange(data, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat]);
app.AppendRange(data_info, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat]);
app.AppendRange(dataTable, "A4:C12", [overwrite], [sheet], [sheetIdx], [numFormat]);
```
{% endtab %}
{% endtabs %}
