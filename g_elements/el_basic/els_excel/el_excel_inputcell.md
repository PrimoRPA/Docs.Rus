# Ввод в ячейку

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (6).png>)

![](<../../../.gitbook/assets/image (450).png>)

Компонент, производящий запись данных в ячейку Excel. Компонент корректно работает только внутри контейнера Приложение Excel.

| Свойство        | Тип     | Описание                      |
| --------------- | ------- | ----------------------------- |
| Страница        | String  | Наименование страницы         |
| Индекс страницы | Int32   | Индекс страницы               |
| Как текст       | Boolean | Вставлять значение, как текст |
| Данные\*        | String  | Данные, вводимые в ячейку     |
| Числовой формат | String  | Формат вводимого числа (#,#)  |
| Ячейка\*        | String  | Идентификатор ячейки (A4)     |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.WriteCell("A1", "text", "Лист1", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.WriteCell("A1", "text", "Лист1", 0)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.WriteCell("A1", "text", "Лист1", 0);
```
{% endtab %}
{% endtabs %}
