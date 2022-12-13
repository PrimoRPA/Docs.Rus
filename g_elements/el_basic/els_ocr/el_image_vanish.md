# Исчезновение изображения

![](<../../../.gitbook/assets/image (423).png>)

Компонент, ожидающий исчезновение заданного изображения на экране. В случае, если значение Искомого изображения не указано, растр берется из скриншота компонента.

| Свойство            | Тип                   | Описание                                           |
| ------------------- | --------------------- | -------------------------------------------------- |
| Искомое изображение | [System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8) | Растр искомого изображения                         |
| Точность            | [Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0) | Точность совпадения растра (% от 0 до 1)           |
| Таймаут\*           | Int32                 | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp.Vanish(wf, (System.Drawing.Bitmap)System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.OCR.OcrApp.Vanish(wf, System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.OCR.OcrApp.Vanish(wf, _lib.System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000);
```
{% endtab %}
{% endtabs %}
