# Записать в ячейку таблицы

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (211).png>)

![](<../../../.gitbook/assets/image (28).png>)

Элемент, записывающий текст в ячейку таблицы. Элемент работает корректно только внутри контейнера Word

| Свойство | Тип    | Описание                 |
| -------- | ------ | ------------------------ |
| Индекс\* | Int32  | Порядковый номер таблицы |
| Данные   | string | Данные ячейки            |
| Строка   | Int32  | Индекс строки            |
| Колонка  | Int32  | Индекс колонки           |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.WriteTableCell(1, "cell", 2, 4);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.WriteTableCell(1, "cell", 2, 4)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.WriteTableCell(1, "cell", 2, 4);
```
{% endtab %}
{% endtabs %}
