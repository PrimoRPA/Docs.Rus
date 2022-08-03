# МойОфис Таблица

![](<../../../../.gitbook/assets/image (529).png>)



Компонент, производящий подключение к приложению МойОфис Таблицы. В случае отсутствия указанного файла, будет создан новый.

| Свойство      | Тип     | Описание                                             |
| ------------- | ------- | ---------------------------------------------------- |
| Путь к файлу  | String  | Путь к файлу документа МойОфис (c:\folder\file.xlsx) |
| Массив байтов | byte\[] | Массив байтов документа                              |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MyOfficeTableApp app = LTools.Office.MyOfficeTableApp.Init(wf, fileName);
LTools.Office.MyOfficeTableApp app = LTools.Office.MyOfficeTableApp.Init(wf, bytes);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MyOfficeTableApp.Init(wf, fileName) #LTools.Office.MyOfficeTableApp
app = LTools.Office.MyOfficeTableApp.Init(wf, bytes) #LTools.Office.MyOfficeTableApp
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Office.MyOfficeTableApp.Init(wf, fileName); //_lib.LTools.Office.MyOfficeTableApp
let app = _lib.LTools.Office.MyOfficeTableApp.Init(wf, bytes); //_lib.LTools.Office.MyOfficeTableApp
```
{% endtab %}
{% endtabs %}
