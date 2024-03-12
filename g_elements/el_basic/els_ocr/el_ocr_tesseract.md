# Tesseract OCR

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (128).png>)

![](<../../../.gitbook/assets/image (309).png>)

Компонент, осуществляющий подключение к ядру OCR Tesseract. Tesseract 3-й версии поставляется вместе с Primo RPA Studio и не требует дополнительной установки.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип                | Описание                                                                                                                                                                |
| --------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Путь к данным\* | String             | Путь к хранилищу данных нейросети '[https://tesseract-ocr.github.io/tessdoc/Data-Files](https://tesseract-ocr.github.io/tessdoc/Data-Files)' (совместим с версией 3.02) |
| Язык\*          | String             | Язык данных нейросети (eng)                                                                                                                                             |
| Масштаб\*       | Int32              | Коэффициент масштабирования изображения                                                                                                                                 |
| Переменная      | LTools.OCR.OCRInst | Переменная для сохранения ссылки на ядро OCR                                                                                                                            |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):


{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitTesseract(wf, "Путь к файлу нейросети", "eng", 2);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitTesseract(wf, "Путь к файлу нейросети", "eng", 2)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = Lib.LTools.OCR.OcrApp.InitTesseract(wf, "Путь к файлу нейросети", "eng", 2);
```
{% endtab %}
{% endtabs %}
