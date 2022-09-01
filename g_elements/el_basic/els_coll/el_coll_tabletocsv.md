# Таблицу в CSV

![](<../../../.gitbook/assets/image (119) (43).png>)

![](<../../../.gitbook/assets/image (435).png>)

Преобразует таблицу к CSV.

| Свойство      | Тип                   | Описание                                             |
| ------------- | --------------------- | ---------------------------------------------------- |
| Таблица\*     | System.Data.DataTable | Таблица данных                                       |
| Разделитель\* | String                | Разделитель колонок                                  |
| Переменная\*  | String                | Переменная для сохранения результатов преобразования |

{% tabs %}
{% tab title="C#" %}
```csharp
System.Data.DataTable table = new System.Data.DataTable();
string ret = LTools.Common.Helpers.DataHelper.DataTableToCSV(table, ";");
```
{% endtab %}

{% tab title="Python" %}
```python
table = System.Data.DataTable()
ret = LTools.Common.Helpers.DataHelper.DataTableToCSV(table, ";")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var table = host.newObj(_lib.System.Data.DataTable);
var ret = _lib.LTools.Common.Helpers.DataHelper.DataTableToCSV(table, ";");
```
{% endtab %}
{% endtabs %}
