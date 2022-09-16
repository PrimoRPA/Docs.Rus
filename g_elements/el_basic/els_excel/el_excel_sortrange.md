# Сортировка диапазона

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (2) (150).png>)

![](<../../../.gitbook/assets/image (336).png>)

Компонент, устанавливающий сортировку диапазона ячеек Excel.

| Свойство        | Тип                                 | Описание                                                                               |
| --------------- | ----------------------------------- | -------------------------------------------------------------------------------------- |
| Диапазон\*      | String                              | Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон |
| Страница        | String                              | Наименование страницы                                                                  |
| Индекс страницы | Int32                               | Индекс страницы                                                                        |
| Направление\*   | LTools.Office.Model. SortDirections | Направление сортировки                                                                 |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SortRange("A1:C12", LTools.Office.Model.SortDirections.ASCENDING, "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SortRange("A1:C12", LTools.Office.Model.SortDirections.ASCENDING, "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SortRange("A1:C12", _lib.LTools.Office.Model.SortDirections.ASCENDING, "Лист1");
```
{% endtab %}
{% endtabs %}
