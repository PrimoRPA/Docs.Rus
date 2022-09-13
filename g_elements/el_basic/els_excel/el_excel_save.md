# Сохранить документ

![](<../../../.gitbook/assets/image (100) (1) (1) (41).png>)

![](<../../../.gitbook/assets/image (283).png>)

Компонент, производящий сохранения файла Excel. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Excel. Компонент корректно работает только внутри контейнера Приложение Excel.

| Свойство     | Тип    | Описание                                  |
| ------------ | ------ | ----------------------------------------- |
| Путь к файлу | String | Путь к файлу Excel (c:\folder\files.xlsx) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file2");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.Save()
app.SaveAs("file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file");
```
{% endtab %}
{% endtabs %}
