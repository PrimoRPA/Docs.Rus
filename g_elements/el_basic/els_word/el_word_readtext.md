# Чтение текста

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (91).png>)

![](<../../../.gitbook/assets/image (55).png>)

Компонент, считывающий данные из документа Word. Компонент корректно работает только внутри контейнера Приложение Word.

| Свойство   | Тип    | Описание                                   |
| ---------- | ------ | ------------------------------------------ |
| Переменная | String | Переменная для хранения результатов чтения |
| Начало     | Int32  | Начало выделения                           |
| Длина      | Int32  | Длина выделения                            |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.WordApp app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX);
string txt = app.ReadText(10, 100);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.WordApp.Init(wf, "file", LTools.Office.Model.InteropTypes.DX)
txt = app.ReadText(10, 100)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.WordApp.Init(wf, "file", _lib.LTools.Office.Model.InteropTypes.DX);
var txt = app.ReadText(10, 100);
```
{% endtab %}
{% endtabs %}
