# Вставить объект

![](<../../../.gitbook/assets/image (483).png>)



Компонент, производящий вставку объекта в презентацию.

Свойства

| Свойство      | Тип     | Описание               |
| ------------- | ------- | ---------------------- |
| Индекс слайда | Int32   | Индекс слайда          |
| Фигура        | String  | Имя фигуры для вставки |
| Слева         | double? | Отступ слева           |
| Сверху        | double? | Отступ сверху          |
| Ширина        | double? | Ширина                 |
| Высота        | double? | Высота                 |

{% tabs %}
{% tab title="C#" %}
```csharp
app.PasteItem(1, "Shape1", 10, 20, 100, 50);
```
{% endtab %}

{% tab title="Python" %}
```python
app.PasteItem(1, "Shape1", 10, 20, 100, 50)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.PasteItem(1, "Shape1", 10, 20, 100, 50);
```
{% endtab %}
{% endtabs %}
