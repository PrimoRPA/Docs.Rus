# Приложение PowerPoint

![](<../../../.gitbook/assets/image (548).png>)



Компонент, производящий подключение к приложению PowerPoint. В случае отсутствия указанного файла, будет создан новый.

Свойства

| Свойство              | Тип     | Описание                                                  |
| --------------------- | ------- | --------------------------------------------------------- |
| Путь к файлу          | String  | Путь к файлу презентации PowerPoint (c:\folder\file.pptx) |
| Массив байтов         | byte\[] | Массив байтов презентации                                 |
| Отображать PowerPoint | Boolean | Отображать приложение PowerPoint на экране                |

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.PowerPoint.PowerPointApp app = Primo.Office.PowerPoint.PowerPointApp.Init(wf, "C:\\file.pptx");
Primo.Office.PowerPoint.PowerPointApp app = Primo.Office.PowerPoint.PowerPointApp.Init(wf, bytes);
```
{% endtab %}

{% tab title="Python" %}
```python
app = Primo.Office.PowerPoint.PowerPointApp.Init(wf, "C:\\file.pptx") #Primo.Office.PowerPoint.PowerPointApp
app = Primo.Office.PowerPoint.PowerPointApp.Init(wf, bytes) #Primo.Office.PowerPoint.PowerPointApp
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.Primo.Office.PowerPoint.PowerPointApp.Init(wf, "C:\\file.pptx"); //_lib.Primo.Office.PowerPoint.PowerPointApp
let app = _lib.Primo.Office.PowerPoint.PowerPointApp.Init(wf, bytes); //_lib.Primo.Office.PowerPoint.PowerPointApp
```
{% endtab %}
{% endtabs %}
