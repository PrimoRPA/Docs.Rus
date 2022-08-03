# Поиск изображения

![](<../../../.gitbook/assets/image (384).png>)

Компонент, производящий поиск заданного изображения на экране.

В случае, если значение Искомого изображения не указано, растр берется из скриншота компонента

| Свойство            | Тип                      | Описание                                           |
| ------------------- | ------------------------ | -------------------------------------------------- |
| Искомое изображение | System.Drawing.Bitmap    | Растр искомого изображения                         |
| Точность            | Double                   | Точность совпадения растра (% от 0 до 1)           |
| Координаты          | System.Drawing.Rectangle | Координаты найденного изображения                  |
| Таймаут\*           | Int32                    | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
System.Drawing.Rectangle coords = LTools.OCR.OcrApp.Exists(wf, (System.Drawing.Bitmap)System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
 app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU")
coords = LTools.OCR.OcrApp.Exists(wf, System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
var coords = _lib.LTools.OCR.OcrApp.Exists(wf, _lib.System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000);
```
{% endtab %}
{% endtabs %}
