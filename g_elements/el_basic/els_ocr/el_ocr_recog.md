# Распознать текст

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (119).png>)

![](<../../../.gitbook/assets/image (316).png>)

Компонент, производящий разбор экранного текста методом OCR.

| Свойство     | Тип                   | Описание                                           |
| ------------ | --------------------- | -------------------------------------------------- |
| Переменная\* | LTools.OCR.OCRInst    | Переменная со ссылкой на ядро OCR                  |
| Изображение  | System.Drawing.Bitmap | Массив байт изображения                            |
| Текст\*      | String                | Переменная для хранения полученного текста         |
| Таймаут\*    | Int32                 | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
string txt = app.GetText((System.Drawing.Bitmap)System.Drawing.Bitmap.FromFile("Файл 1"), 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU")
txt = app.GetText(System.Drawing.Bitmap.FromFile("Файл 1"), 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
var txt = app.GetText(_lib.System.Drawing.Bitmap.FromFile("Файл 1"), 10000);
```
{% endtab %}
{% endtabs %}
