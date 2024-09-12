# Распознать текст

![](<../../../.gitbook/assets/image (316).png>)

Элемент производит разбор экранного текста методом OCR.

## Свойства

Символ `*` в названии указывает на обязательность заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                   | Описание                                           |
| ------------ | --------------------- | -------------------------------------------------- |
| Переменная\* | LTools.OCR.OCRInst    | Переменная со ссылкой на ядро OCR                  |
| Изображение  | System.Drawing.Bitmap | Массив байт изображения                            |
| Текст\*      | String                | Переменная для хранения полученного текста         |
| Таймаут\*    | Int32                 | Предельное время ожидания завершения процесса (мс) |

## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код (Pure code)**:

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
