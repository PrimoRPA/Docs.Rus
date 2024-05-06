# Ввод текста


![](<../../../.gitbook/assets/image (171).png>)

Компонент, производящий запись данных в документ Word. Компонент корректно работает только внутри контейнера Приложение Word.

| Свойство | Тип    | Описание                                                                                      |
| -------- | ------ | --------------------------------------------------------------------------------------------- |
| Закладка | String | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Начало   | Int32  | Индекс начала вставки                                                                         |
| Текст\*  | String | Данные, вводимые в документ                                                                   |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.AppendText("text", 10);
app.AppendText("text", "bookmark");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.AppendText("text", 10)
app.AppendText("text", "bookmark")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.AppendText("text", 10);
app.AppendText("text", "bookmark");
```
{% endtab %}
{% endtabs %}
