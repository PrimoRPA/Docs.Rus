# Вставить медиа-файл

![](<../../../.gitbook/assets/image (533).png>)



Компонент, производящий вставку медиа-файла в презентацию.


| Свойство      | Тип     | Описание               |
| ------------- | ------- | ---------------------- |
| Индекс слайда | Int32   | Индекс слайда          |
| Фигура        | String  | Имя фигуры для вставки |
| Файл          | String  | Путь к файлу           |
| Слева         | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)? | Отступ слева           |
| Сверху        | double? | Отступ сверху          |
| Ширина        | double? | Ширина                 |
| Высота        | double? | Высота                 |

> Символ ? в типе данных указывает на то, что значение может быть null.

{% tabs %}
{% tab title="C#" %}
```csharp
app.AddMedia(1, "Shape1", "C:\\file.avi", 10, 20, 100, 50);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AddMedia(1, "Shape1", "C:\\file.avi", 10, 20, 100, 50)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AddMedia(1, "Shape1", "C:\\file.avi", 10, 20, 100, 50);
```
{% endtab %}
{% endtabs %}
