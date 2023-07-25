# Получение изображений

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (201).png>)

![](<../../../.gitbook/assets/image (338).png>)

Компонент, получающий изображения из документа PDF

| Свойство       | Тип                          | Описание                                   |
| -------------- | ---------------------------- | ------------------------------------------ |
| Путь к файлу\* | String                       | Путь к файлу PDF                           |
| Пароль         | String                       | Пароль документа PDF                       |
| Страницы       | String                       | Номера страниц документа (1,2,4)           |
| Переменная     | List\<System.Drawing.Bitmap> | Переменная для хранения результатов чтения |

{% tabs %}
{% tab title="C#" %}
```csharp
List<System.Drawing.Bitmap> img = LTools.Office.PdfApp.ReadImages(wf, "Файл 1", "пароль", "1,2");
```
{% endtab %}

{% tab title="Python" %}
```python
img = LTools.Office.PdfApp.ReadImages(wf, "Файл 1", "пароль", "1,2")
```
{% endtab %}

{% tab title="JavaScipt" %}
```javascript
var img = _lib.LTools.Office.PdfApp.ReadImages(wf, "Файл 1", "пароль", "1,2");
```
{% endtab %}
{% endtabs %}
