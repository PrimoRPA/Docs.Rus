# Запись диапазона

![](<../../../.gitbook/assets/image (495).png>)

![](<../../../.gitbook/assets/image (28).png>)

Компонент, записывающий данные диапазона ячеек в Excel.

| Свойство                | Тип                                                                          | Описание                                                        |
| ----------------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------- |
| Диапазон\*              | String                                                                       | Диапазон считывания ячеек (A1:D12)                              |
| Добавлять заголовки     | Boolean                                                                      | Добавлять заголовки колонок таблицы                             |
| Страница                | String                                                                       | Наименование страницы                                           |
| Индекс страницы         | Int32                                                                        | Индекс страницы                                                 |
| Как текст               | Boolean                                                                      | Вставлять значение, как текст                                   |
| Перезаписать            | Boolean                                                                      | Признак перезаписи данных                                       |
| Направление             |                                                                              | Направление сдвига ячеек                                        |
| Раширять диапазон       |                                                                              | Автоматически расширять диапазон до размеров данных             |
| Переменная (текст)      | List\<List\<string>>                                                         | Переменная для хранения результатов чтения текстовых значений   |
| Переменная (информация) | List\<List<[LTools.Office.Model.ExcelCellInfo](datatypes/excelcellinfo.md)>> | Переменная для хранения результатов чтения информации о ячейках |
| Переменная (таблица)    | System.Data.DataTable                                                        | Переменная для хранения данных текстовых значений               |
| Числовой формат         | String                                                                       | Формат вводимого числа (#,#)                                    |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.AppendRange(new List<List<string>>(), "A1:B2", true, "Лист1", 0);
app.AppendRange(new List<List<LTools.Office.Model.ExcelCellInfo>>(), "A1:B2", true, null, 0);
app.AppendRange(new System.Data.DataTable(), "A1:B2", true, "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
dt = List[List[String]]()
dt2 = List[List[LTools.Office.Model.ExcelCellInfo]]()
app.AppendRange(dt, "A1:B2", true, "Лист1", 0)
app.AppendRange(dt2, "A1:B2", true, null, 0)
app.AppendRange(System.Data.DataTable(), "A1:B2", true, "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.AppendRange(lst, "A1:B2", true, "Лист1", 0);
app.AppendRange(lst2, "A1:B2", true, null, 0);
app.AppendRange(lst3, "A1:B2", true, "Лист1");
```
{% endtab %}
{% endtabs %}

