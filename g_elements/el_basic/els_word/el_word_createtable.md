# Вставить таблицу

![](<../../../.gitbook/assets/image (130).png>)

Элемент, вставляющий таблицу в документ. Элемент работает корректно только внутри контейнера Word

| Свойство | Тип                   | Описание                                                                                      |
| -------- | --------------------- | --------------------------------------------------------------------------------------------- |
| Закладка | String                | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Данные   | List\<List\<String>>  | Данные таблицы                                                                                |
| Таблица  | System.Data.DataTable | Данные таблицы                                                                                |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.InsertTable(new List<List<String>>(), "bookmark");
app.InsertTable(new System.Data.DataTable(), "bookmark");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.InsertTable(List[List[String]](), "bookmark")
app.InsertTable(System.Data.DataTable(), "bookmark")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var tbl = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.InsertTable(lst, "bookmark");
app.InsertTable(tbl, "bookmark");
```
{% endtab %}
{% endtabs %}
