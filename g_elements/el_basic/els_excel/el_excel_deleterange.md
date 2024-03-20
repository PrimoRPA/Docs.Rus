# Удаление диапазона


![](<../../../.gitbook/assets/image (97).png>)

Компонент, удаляющий диапазон ячеек в Excel.

| Свойство        | Тип     | Описание                                                                                  |
| --------------- | ------- | ----------------------------------------------------------------------------------------- |
| Диапазон\*      | String  | Диапазон удаления ячеек (A1:D12)                                                          |
| Страница        | String  | Наименование страницы                                                                     |
| Индекс страницы | Int32   | Индекс страницы                                                                           |
| Только ячейки   | Boolean | Признак того, что будут уничтожены только ячейки диапазона, а не колонки и строки целиком |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.RemoveRange("A1:C12", true, "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.RemoveRange("A1:C12", True, "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.RemoveRange("A1:C12", true, "Лист1");
```
{% endtab %}
{% endtabs %}
