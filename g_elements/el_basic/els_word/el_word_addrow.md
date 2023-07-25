# Добавить строку таблицы

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (92).png>)

![](<../../../.gitbook/assets/image (139).png>)

Элемент, добавляющий строку к таблице. Элемент работает корректно только внутри контейнера Word

| Свойство | Тип                 | Описание                 |
| -------- | ------------------- | ------------------------ |
| Индекс\* | Int32               | Порядковый номер таблицы |
| Данные   | List\<String>       | Данные строки            |
| Строка   | System.Data.DataRow | Данные строки            |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.AddTableRow(0, new List<String> { "cell1" });
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
dt.Add("cell1")
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.AddTableRow(0, dt)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("cell1");
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.AddTableRow(0, lst);
```
{% endtab %}
{% endtabs %}
