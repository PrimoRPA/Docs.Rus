# Прочитать таблицу

![](<../../../.gitbook/assets/image (168).png>)

Элемент, читающий таблицу из документа. Элемент работает корректно только внутри контейнера Word

| Свойство  | Тип                   | Описание                 |
| --------- | --------------------- | ------------------------ |
| Индекс\*: | Int32                 | Порядковый номер таблицы |
| Данные    | List\<List\<String>>  | Данные таблицы           |
| Таблица   | System.Data.DataTable | Данные таблицы           |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
List<List<string>> list = app.ReadTableArr(1);
System.Data.DataTable table = app.ReadTable(1);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
list = app.ReadTableArr(1)
table = app.ReadTable(1)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
var list = app.ReadTableArr(1);
var table = app.ReadTable(1);
```
{% endtab %}
{% endtabs %}
