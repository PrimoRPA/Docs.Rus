# Фильтр диапазона

![](<../../../.gitbook/assets/image (265).png>)

Компонент, устанавливающий фильтр диапазона ячеек Excel.

| Свойство        | Тип           | Описание                                                                               |
| --------------- | ------------- | -------------------------------------------------------------------------------------- |
| Диапазон\*      | String        | Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон |
| Страница        | String        | Наименование страницы                                                                  |
| Индекс страницы | Int32         | Индекс страницы                                                                        |
| Фильтр\*        | List\<string> | Значения фильтра                                                                       |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.FilterRange(new List<string>(), "A1:C12", "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.FilterRange(List[String](), "A1:C12", "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.FilterRange(lst, "A1:C12", "Лист1");
```
{% endtab %}
{% endtabs %}
