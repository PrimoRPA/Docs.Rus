# Заменить текст


![](<../../../.gitbook/assets/image (128).png>)

Заменяет все вхождения исходного текста на новый.

| Свойство       | Тип    | Описание                 |
| -------------- | ------ | ------------------------ |
| Исходный текст | String | Текст, подлежащий замене |
| Новый текст\*  | String | Новый текст              |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
app.ReplaceText("oldText", "newText");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
app.ReplaceText("oldText", "newText")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
app.ReplaceText("oldText", "newText");
```
{% endtab %}
{% endtabs %}
