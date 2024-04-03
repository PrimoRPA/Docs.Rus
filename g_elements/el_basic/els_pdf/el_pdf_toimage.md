# Преобразовать в изображение

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (41).png>)

![](<../../../.gitbook/assets/image (322).png>)

Компонент, преобразующий документ PDF в изображения.

| Свойство       | Тип                           | Описание                                           |
| -------------- | ----------------------------- | -------------------------------------------------- |
| Путь к файлу\* | String                        | Путь к файлу PDF                                   |
| Пароль         | String                        | Пароль документа PDF                               |
| Размер\*       | int                           | Длина наибольшей стороны изображения (пиксели)     |
| Страницы       | String                        | Массив извлекаемых страниц (1,2,4)                 |
| Переменная     | List \<System.Drawing.Bitmap> | (Windows) Переменная для хранения результатов преобразования |
| Переменная     | SixLabors.ImageSharp.Image    | (Linux) Переменная для хранения результатов преобразования |

{% tabs %}
{% tab title="C#" %}
```csharp
List<System.Drawing.Bitmap> img = LTools.Office.PdfApp.ConvertToImage(wf, "Файл 1", 2000, "пароль");
```
{% endtab %}

{% tab title="Python" %}
```python
img = LTools.Office.PdfApp.ConvertToImage(wf, "Файл 1", 2000, "пароль")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var img = _lib.LTools.Office.PdfApp.ConvertToImage(wf, "Файл 1", 2000, "пароль");
```
{% endtab %}
{% endtabs %}
