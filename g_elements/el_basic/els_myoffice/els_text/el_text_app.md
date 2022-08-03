# МойОфис Текст

![](<../../../../.gitbook/assets/image (938).png>)

Компонент, производящий подключение к приложению Текст. В случае отсутствия указанного файла, будет создан новый.

| Свойство      | Тип     | Описание                                           |
| ------------- | ------- | -------------------------------------------------- |
| Путь к файлу  | String  | Путь к файлу документа Текст (c:\folder\file.docx) |
| Массив байтов | byte\[] | Массив байтов документа                            |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MyOfficeTextApp app = LTools.Office.MyOfficeTextApp.Init(wf, fileName, [interop]);
LTools.Office.MyOfficeTextApp app = LTools.Office.MyOfficeTextApp.Init(wf, bytes);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MyOfficeTextApp.Init(wf, fileName) #LTools.Office.MyOfficeTextApp
app = LTools.Office.MyOfficeTextApp.Init(wf, bytes) #LTools.Office.MyOfficeTextApp
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Office.MyOfficeTextApp.Init(wf, fileName); //_lib.LTools.Office.MyOfficeTextApp
let app = _lib.LTools.Office.MyOfficeTextApp.Init(wf, bytes); //_lib.LTools.Office.MyOfficeTextApp
```
{% endtab %}
{% endtabs %}
