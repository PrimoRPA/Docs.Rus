# Цвет фона шрифта

![](<../../../.gitbook/assets/image (524).png>)



Элемент, обрабатывающий цвет фона текста документа.

Свойства

| Свойство    | Тип                  | Описание                  |
| ----------- | -------------------- | ------------------------- |
| Новый цвет  | System.Drawing.Color | Устанавливаемый цвет фона |
| Менять цвет | Boolean              | Признак изменения цвета   |
| Цвет        | System.Drawing.Color | Текущий цвет фона         |
| Начало      | Int32                | Начало текста             |
| Длина       | Int32                | Длина текста              |

{% tabs %}
{% tab title="C#" %}
```csharp
System.Drawing.Color color = app.GetTextBackground(10, 25);
app.SetTextBackground(10, 25, new System.Drawing.Color(255, 100, 0, 0));
```
{% endtab %}

{% tab title="Python" %}
```python
color = app.GetTextBackground(10, 25); #System.Drawing.Color
app.SetTextBackground(10, 25, System.Drawing.Color(255, 100, 0, 0))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var color = app.GetTextBackground(10, 25); //_lib.System.Drawing.Color
app.SetTextBackground(10, 25, clr);
```
{% endtab %}
{% endtabs %}
