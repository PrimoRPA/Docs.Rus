# Чтение диапазона

![](<../../../../.gitbook/assets/image (458).png>)

Компонент, считывающий данные из диапазона ячеек Таблицы.

| Свойство                | Тип                                                                                            | Описание                                                                                                                                  |
| ----------------------- | ---------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Диапазон                | String                                                                                         | Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон. Если указан символ "\*", будет прочитан весь лист |
| Страница                | String                                                                                         | Наименование страницы                                                                                                                     |
| Индекс страницы         | Int32                                                                                          | Индекс страницы                                                                                                                           |
| Переменная (текст)      | List\<List\<String>>                                                                           | Переменная для хранения результатов чтения текстовых значений                                                                             |
| Переменная (информация) | List\<List<[LTools.Office. Model.ExcelCellInfo](../../els\_excel/datatypes/excelcellinfo.md)>> | Переменная для хранения результатов чтения информации о ячейках                                                                           |
| Переменная (таблица)    | System.Data.DataTable                                                                          | Переменная для хранения результатов чтения текстовых значений                                                                             |
| Строка заголовков       | Boolean                                                                                        | Признак того, что первая строка содержит заголовки (для таблицы)                                                                          |

{% tabs %}
{% tab title="C#" %}
```csharp
List<List<string>> data = app.ReadRange("A4:C12", [sheet], [sheetIdx]);
List<List<LTools.Office.Model.ExcelCellInfo>> data = app.ReadRangeInfo("A4:C12", [sheet], [sheetIdx]);
System.Data.DataTable data = app.ReadRangeTable("A4:C12", [sheet], [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
data = app.ReadRange("A4:C12", [sheet], [sheetIdx]) #List<List<string>>
data = app.ReadRangeInfo("A4:C12", [sheet], [sheetIdx]) #List<List<LTools.Office.Model.ExcelCellInfo>>
data = app.ReadRangeTable("A4:C12", [sheet], [sheetIdx]) #System.Data.DataTable
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let data = app.ReadRange("A4:C12", [sheet], [sheetIdx]); //List<List<string>>
let data = app.ReadRangeInfo("A4:C12", [sheet], [sheetIdx]); //List<List<LTools.Office.Model.ExcelCellInfo>>
let data = app.ReadRangeTable("A4:C12", [sheet], [sheetIdx]); //System.Data.DataTable
```
{% endtab %}
{% endtabs %}
