# Запустить макрос

![](<../../../.gitbook/assets/image (350).png>)

Элемент, выполняющий макрос Excel.

| Свойство       | Тип           | Описание             |
| -------------- | ------------- | -------------------- |
| Наименование\* | String        | Наименование макроса |
| Аргументы\*    | List\<object> | Аргументы макроса    |
| Видимость\*    | Boolean       | Видимость Excel      |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.RunMacro("macro", null, true);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.RunMacro("macro", null, true)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.RunMacro("macro", null, true);
```
{% endtab %}
{% endtabs %}
