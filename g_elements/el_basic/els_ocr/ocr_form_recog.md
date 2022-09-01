# Распознать форму

![](<../../../.gitbook/assets/image (286).png>)

Компонент, производящий разбор формы текста по шаблону методом OCR. Если параметр Изображение не указан, будет сделан скриншот всего экрана. Для работы с шаблонами можно использовать инструмент [Редактор шаблонов OCR.](../../../primo-studio/tools/ocr-template-editor.md)

| Свойство     | Тип                                                                   | Описание                                           |
| ------------ | --------------------------------------------------------------------- | -------------------------------------------------- |
| Переменная\* | LTools.OCR.OCRInst                                                    | Переменная со ссылкой на ядро OCR                  |
| Изображение  | System.Drawing.Bitmap                                                 | Массив байт изображения                            |
| Текст\*      | [LTools.OCR.Model. OCRPatternResults](datatypes/ocrpatternresults.md) | Переменная для хранения полученного текста         |
| Шаблон\*     | String                                                                | Путь к файлу шаблона                               |
| Таймаут\*    | Int32                                                                 | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
LTools.OCR.Model.OCRPatternResults res = app.GetPattern((System.Drawing.Bitmap)System.Drawing.Bitmap.FromFile("Файл 1"), "Шаблон 1", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU")
res = app.GetPattern(System.Drawing.Bitmap.FromFile("Файл 1"), "Шаблон 1", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
var res = app.GetPattern(_lib.System.Drawing.Bitmap.FromFile("Файл 1"), "Шаблон 1", 10000);
```
{% endtab %}
{% endtabs %}

