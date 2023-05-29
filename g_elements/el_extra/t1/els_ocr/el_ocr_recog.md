# Распознать текст

![](<../../../../.gitbook/assets/get_ocrtext.png>)

Элемент производит разбор изображения на экране методом OCR и извлекает из него текстовые данные. Если параметр c изображением не задан, будет сделан скриншот всего экрана.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***OCR:*** | |  |
| Переменная\* | Primo.T1.OCR.OCRInst | Переменная со ссылкой на ядро OCR. При использовании элемента внутри контейнера [Microsoft OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/t1/els_ocr/el_ocr_microsoft) или [Tesseract OCR](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/t1/els_ocr/el_ocr_tesseract) свойство можно не заполнять |
| ***Прочее:***  |  |  |
| Bmp | [System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?view=windowsdesktop-7.0) | Массив байт изображения |
| ***Вывод:***  |  |  |
| Текст | String | Переменная для хранения полученного текста |
| Блоки  | [List\<KeyValuePair\<Rectangle, string\>\>](https://learn.microsoft.com/ru-Ru/dotnet/api/system.collections.generic.keyvaluepair-2?view=netframework-4.6.1) | Переменная для хранения блоков текста |
