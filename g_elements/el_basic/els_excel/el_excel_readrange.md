# Чтение диапазона

![](<../../../.gitbook/assets/image (100) (1) (10) (139).png>)

![](<../../../.gitbook/assets/image (75).png>)

Компонент, считывающий данные из диапазона ячеек Excel.

| Свойство                | Тип                                              | Описание                                                                                                                                  |
| ----------------------- | ------------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------- |
| Диапазон                | String                                           | Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон. Если указан символ "\*", будет прочитан весь лист |
| Страница                | String                                           | Наименование страницы                                                                                                                     |
| Индекс страницы         | Int32                                            | Индекс страницы                                                                                                                           |
| Строка заголовков       | Boolean                                          | Признак того, что первая строка содержит заголовки (для таблицы)                                                                          |
| Переменная (текст)      | List\<List\<string>>                             | Переменная для хранения результатов чтения текстовых значений                                                                             |
| Переменная (информация) | List\<List \<LTools.Office.Model.ExcelCellInfo>> | Переменная для хранения результатов чтения информации о ячейках                                                                           |
| Переменная (таблица)    | System.Data.DataTable                            | Переменная для хранения результатов чтения текстовых значений                                                                             |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
List<List<string>> data = app.ReadRange("A1:C12", "Лист1");
List<List<LTools.Office.Model.ExcelCellInfo>> data = app.ReadRangeInfo("A1:C12", "Лист1");
System.Data.DataTable data = app.ReadRangeTable("A1:C12", "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
data = app.ReadRange("A1:C12", "Лист1")
data = app.ReadRangeInfo("A1:C12", "Лист1")
data = app.ReadRangeTable("A1:C12", "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var data = app.ReadRange("A1:C12", "Лист1");
var data = app.ReadRangeInfo("A1:C12", "Лист1");
var data = app.ReadRangeTable("A1:C12", "Лист1");
```
{% endtab %}
{% endtabs %}
