# Чтение диапазона

![](<../../../.gitbook/assets/image (360).png>)

Компонент, считывающий данные из диапазона ячеек Google Sheets.

| Свойство                | Тип                                                                                        | Описание                                                                               |
| ----------------------- | ------------------------------------------------------------------------------------------ | -------------------------------------------------------------------------------------- |
| Диапазон                | String                                                                                     | Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон |
| Страница                | String                                                                                     | Наименование страницы                                                                  |
| Переменная (текст)      | List\<List\<string>>                                                                       | Переменная для хранения результатов чтения текстовых значений                          |
| Переменная (информация) | List\<List<[LTools.Office.Model.ExcelCellInfo](../els\_excel/datatypes/excelcellinfo.md)>> | Переменная для хранения результатов чтения информации о ячейках                        |
| Переменная (таблица)    | System.Data.DataTable                                                                      | Переменная для хранения результатов чтения текстовых значений                          |
| Строка заголовков       | bool                                                                                       | Признак того, что первая строка содержит заголовки (для таблицы)                       |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.GoogleSheetsApp app = LTools.Office.GoogleSheetsApp.Init(wf, @"Путь к токену", @"ID документа");
//Массив строк
List<List<string>> data = app.ReadRange("A1:B1", "Лист1");
//Массив с данными ячеек
List<List<LTools.Office.Model.ExcelCellInfo>> data2 = app.ReadRangeInfo("A1:B1", "Лист1");
//Таблица
System.Data.DataTable data3 = app.ReadRangeTable("A1:B1", "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.GoogleSheetsApp.Init(wf, "Путь к файлу токена", "ID документа")
#Массив строк
data = app.ReadRange("A1:B1", "Лист1")
#Массив с данными ячеек
data2 = app.ReadRangeInfo("A1:B1", "Лист1")
#Таблица
data3 = app.ReadRangeTable("A1:B1", "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Office.GoogleSheetsApp.Init(wf, "Путь к файлу токена", "ID документа");
//Массив строк
var data = app.ReadRange("A1:B1", "Лист1");
//Массив с данными ячеек
var data2 = app.ReadRangeInfo("A1:B1", "Лист1");
//Таблица
var data3 = app.ReadRangeTable("A1:B1", "Лист1");
```
{% endtab %}
{% endtabs %}
