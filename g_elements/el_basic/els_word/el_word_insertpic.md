# Вставка изображения

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (2) (40).png>)

![](<../../../.gitbook/assets/image (204).png>)

Компонент, производящий вставку изображения в документ Word.

| Свойство      | Тип     | Описание                                                                                      |
| ------------- | ------- | --------------------------------------------------------------------------------------------- |
| Закладка      | String  | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Изображение\* | byte\[] | Вставляемое изображение                                                                       |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.InsertPicture(System.IO.File.ReadAllBytes("file"), "bookmark");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.InsertPicture(System.IO.File.ReadAllBytes("file"), "bookmark")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.InsertPicture(_lib.System.IO.File.ReadAllBytes("file"), "bookmark");
```
{% endtab %}
{% endtabs %}
