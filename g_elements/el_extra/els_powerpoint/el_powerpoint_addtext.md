# Вставить текст

![](<../../../.gitbook/assets/image (468).png>)



Компонент, производящий вставку текста в презентацию.

Свойства

| Свойство      | Тип     | Описание                |
| ------------- | ------- | ----------------------- |
| Индекс слайда | Int32   | Индекс слайда           |
| Фигура        | String  | Имя фигуры для вставки  |
| Текст         | String  | Текст                   |
| Очищать       | Boolean | Очищать имеющийся текст |

{% tabs %}
{% tab title="C#" %}
```csharp
app.AddText(1, "Shape1", "text", false);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AddText(1, "Shape1", "text", False)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AddText(1, "Shape1", "text", false);
```
{% endtab %}
{% endtabs %}
