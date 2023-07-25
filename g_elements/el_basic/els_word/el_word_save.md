# Сохранить документ

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (301).png>)

![](<../../../.gitbook/assets/image (217).png>)

Компонент, производящий сохранения файла Word. Если путь к файлу не указан, сохранен будет файл, открытый в рамках текущего контейнера Word. Компонент корректно работает только внутри контейнера Приложение Word.

| Свойство     | Тип    | Описание                                 |
| ------------ | ------ | ---------------------------------------- |
| Путь к файлу | String | Путь к файлу Word (c:\folder\files.docx) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.Save()
app.SaveAs("file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file");
```
{% endtab %}
{% endtabs %}
