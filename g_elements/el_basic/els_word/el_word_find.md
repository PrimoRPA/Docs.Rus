# Найти текст

![](<../../../.gitbook/assets/image (104).png>)

Ищет вхождение заданного текста в документ.

| Свойство            | Тип          | Описание                                                  |
| ------------------- | ------------ | --------------------------------------------------------- |
| Текст               | String       | Искомый текст                                             |
| Переменная          | Int32        | Переменная для хранения индекса первого вхождения текста  |
| Переменная (массив) | List\<Int32> | Переменная для хранения массива индексов вхождения текста |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
List<int> idxs = app.FindText("text");
int? idx = app.FindTextFirst("text");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
idxs = app.FindText("text")
idx = app.FindTextFirst("text")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
var idxs = app.FindText("text");
var idx = app.FindTextFirst("text");
```
{% endtab %}
{% endtabs %}
