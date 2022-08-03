# Вставить файл

![](<../../../.gitbook/assets/image (605).png>)



Компонент, производящий вставку файла в презентацию.

Свойства

| Свойство      | Тип    | Описание               |
| ------------- | ------ | ---------------------- |
| Индекс слайда | Int32  | Индекс слайда          |
| Фигура        | String | Имя фигуры для вставки |
| Файл          | String | Путь к файлу           |
| Заголовок     | String | Заголовок иконки файла |

{% tabs %}
{% tab title="C#" %}
```csharp
app.AddFile(1, "Shape1", "C:\\file.txt", "File title");
```
{% endtab %}

{% tab title="Python" %}
```python
app.AddFile(1, "Shape1", "C:\\file.txt", "File title")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AddFile(1, "Shape1", "C:\\file.txt", "File title");
```
{% endtab %}
{% endtabs %}
