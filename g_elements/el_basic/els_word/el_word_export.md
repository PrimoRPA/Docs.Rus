# Экспортировать документ

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (93).png>)

![](<../../../.gitbook/assets/image (66).png>)

Компонент, производящий экспорт документа Word в другой формат. Доступный формат: PDF

| Свойство     | Тип                                   | Описание                           |
| ------------ | ------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                | Путь к файлу (c:\folder\files.pdf) |
| Формат       | LTools.Office.Model.WordExportFormats | Тип формата                        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.Export("file", LTools.Office.Model.WordExportFormats.Pdf);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.Export("file", LTools.Office.Model.WordExportFormats.Pdf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.Export("file", _lib.LTools.Office.Model.WordExportFormats.Pdf);
```
{% endtab %}
{% endtabs %}
