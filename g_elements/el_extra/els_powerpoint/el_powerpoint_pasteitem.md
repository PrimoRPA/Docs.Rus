# Вставить объект

![](<../../../.gitbook/assets/image (744).png>)



Компонент, производящий вставку объекта в презентацию.

Свойства

| Свойство      | Тип     | Описание               |
| ------------- | ------- | ---------------------- |
| Индекс слайда | Int32   | Индекс слайда          |
| Фигура        | String  | Имя фигуры для вставки |
| Слева         | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)? | Отступ слева           |
| Сверху        | double? | Отступ сверху          |
| Ширина        | double? | Ширина                 |
| Высота        | double? | Высота                 |

Символ ? в типе данных указывает на то, что значение может быть null.

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
