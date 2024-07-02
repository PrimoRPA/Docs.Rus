# Tesseract OCR

![](<../../../.gitbook/assets/image (309).png>)

Компонент осуществляет подключение к ядру OCR Tesseract. Tesseract 3-й версии поставляется вместе с Primo RPA Studio и не требует дополнительной установки.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип                | Описание                                                                                                                                                                |
| --------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Путь к данным\* | String             | Данные для нейросети вы можете найти [на нашем облаке](https://disk.primo-rpa.ru/index.php/s/t9BHBjR6PP06Yax?path=%2FMisc) — скачайте архив `tesseract-ocr.zip`, после чего укажите в этом свойстве путь до папки с данными. Пример: `@"C:\Users\name\tesseract-ocr\tessdata"` <br>Если вы используете данные из другого источника, то они должны быть совместимы с версией Tesseract 3.02</br> |
| Язык\*          | String             | Язык данных нейросети. Пример: `"rus"`                                                                                                                                             |
| Масштаб\*       | Int32              | Коэффициент масштабирования изображения                                                                                                                                 |
| Переменная      | LTools.OCR.OCRInst | Название переменной, в которой сохранится ссылка на ядро OCR                                                                                                                            |


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
