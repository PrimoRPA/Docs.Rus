# Цвет шрифта

![](<../../../.gitbook/assets/image (608).png>)



Элемент, обрабатывающий цвет текста документа.

Свойства

| Свойство    | Тип                  | Описание                |
| ----------- | -------------------- | ----------------------- |
| Новый цвет  | System.Drawing.Color | Устанавливаемый цвет    |
| Менять цвет | Boolean              | Признак изменения цвета |
| Цвет        | System.Drawing.Color | Текущий цвет            |
| Начало      | Int32                | Начало текста           |
| Длина       | Int32                | Длина текста            |

{% tabs %}
{% tab title="C#" %}
```csharp
System.Drawing.Color color = app.GetTextColor(10, 25);
app.SetTextColor(10, 25, new System.Drawing.Color(255, 100, 0, 0));
```
{% endtab %}

{% tab title="Python" %}
```python
color = app.GetTextColor(10, 25) #System.Drawing.Color
app.SetTextColor(10, 25, System.Drawing.Color(255, 100, 0, 0))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var color = app.GetTextColor(10, 25); //_lib.System.Drawing.Color
app.SetTextColor(10, 25, clr);
```
{% endtab %}
{% endtabs %}
