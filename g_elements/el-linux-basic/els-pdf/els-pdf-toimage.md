---
description: Convert PDF to image
---

# Преобразовать в изображение

![](<../../../.gitbook/assets1/PDF-ConvertToImage.png>)

Компонент, преобразующий документ PDF в изображение.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Путь к файлу\*** *[String]* - Путь к файлу PDF  
1. **Пароль** *[String]* - Пароль документа PDF  
1. **Защищенный пароль** *[SecureString]* - Защищенный пароль
1. **Размер\*** *[int]* - Длина наибольшей стороны изображения (пиксели)  
1. **Страницы\*** *[String]* - Массив извлекаемых страниц (1,2,4)  
1. **Переменная** *[List<SixLabors.ImageSharp.Image>]* - Переменная для хранения результатов преобразования  

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

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
