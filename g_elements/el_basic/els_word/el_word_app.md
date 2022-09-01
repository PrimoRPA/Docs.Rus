# Документ Word

![](<../../../.gitbook/assets/image (119) (134).png>)

![](<../../../.gitbook/assets/image (169).png>)

Компонент, производящий подключение к приложению Word. В случае отсутствия указанного файла, будет создан новый.

| Свойство      | Тип                               | Описание                                          |
| ------------- | --------------------------------- | ------------------------------------------------- |
| Путь к файлу  | String                            | Путь к файлу документа Word (c:\folder\file.docx) |
| Драйвер       | LTools.Office.Model. InteropTypes | Тип драйвера подключения                          |
| Массив байтов | byte\[]                           | Массив байтов документа                           |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, System.IO.File.ReadAllBytes("file"), LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app = LTools.Office.WordApp.Init(wf, System.IO.File.ReadAllBytes("file"), LTools.Office.Model.InteropTypes.DX)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
var app = _lib.LTools.Office.WordApp.Init(wf, _lib.System.IO.File.ReadAllBytes("file"), _lib.LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}
{% endtabs %}
