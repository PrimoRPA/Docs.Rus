# Приложение Excel

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (123).png>)

![](<../../../.gitbook/assets/image (412).png>)

Компонент, производящий подключение к приложению Excel. В случае отсутствия указанного файла, будет создан новый.

| Свойство         | Тип                               | Описание                                                                             |
| ---------------- | --------------------------------- | ------------------------------------------------------------------------------------ |
| Драйвер          | LTools.Office.Model. InteropTypes | Тип драйвера подключения                                                             |
| Путь к файлу     | String                            | Путь к файлу документа Excel (c:\folder\file.xlsx)                                   |
| Массив байтов    | byte\[]                           | Массив байтов документа                                                              |
| Разделитель      | String                            | Разделитель колонок. Для режима Interop необходима кодировка UTF-8 BOM или UTF-16 LE |
| Отображать Excel | Boolean                           | Отображать приложение Excel на экране (только для Interop)                           |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"), ";", LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app = LTools.Office.ExcelApp.Init(wf, System.IO.File.ReadAllBytes("file"), ";", LTools.Office.Model.InteropTypes.DX)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var app = _lib.LTools.Office.ExcelApp.Init(wf, _lib.System.IO.File.ReadAllBytes("file"), ";", _lib.LTools.Office.Model.InteropTypes.DX);
```
{% endtab %}
{% endtabs %}
