# Tesseract OCR

![](<../../../../.gitbook/assets/google_ocr.png>)

Элемент осуществляет подключение к ядру OCR программы Tesseract. Поддерживается только Tesseract 5-й версии. 

Является контейнером для таких OCR-элементов, как [Клик текста мышью](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/t1/els_ocr/el_ocr_textclick) и [Распознать текст](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_extra/t1/els_ocr/el_ocr_recog).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                                      |
| -------------------- | --------------------- | --------------------------------------------- |
| ***OCR:*** | |  |
| Язык | String | Язык для извлечения текста из изображения или элемента UI, указать можно только 1. По умолчанию `"eng"` (коды можно просмотреть [здесь](https://github.com/tesseract-ocr/tesseract/blob/main/doc/tesseract.1.asc#languages)). Папку с языковыми данными нейросети можно [скачать](https://tesseract-ocr.github.io/tessdoc/Data-Files). |
| Масштаб | Double | Коэффициент масштабирования изображения. Рекомендуется использовать для небольших изображений. Значение `1.00` соответствует оригинальному размеру. Чем выше число, тем больше масштаб |
| Путь к данным |  | Путь к хранилищу данных нейросети, расположенному по [ссылке](https://tesseract-ocr.github.io/tessdoc/Data-Files) (совместим с версией 5.0) |
| ***Вывод:***  |  |  |
| Переменная | Primo.T1.OCR.OCRInst | Переменная для сохранения ссылки на ядро OCR |

## Решение проблем
* При возникновении ошибки с файлом `libdl` иногда она может быть решена с помощью выполнения команды:  
`sudo ln -s /usr/lib/x86_64-linux-gnu/libglu.so.2 /usr/lib/x86_64-linux-gnu/libdl.so`
* В некоторых случаях для работы Tesseract OCR для Linux может потребоваться установка дополнительных пакетов:  
`libtesseract-dev`  
`libleptonica-dev`  
`liblept5`  
После установки пакетов нужно скопировать (и переименовать) файлы:  
`/usr/lib/libleptonica.so.6.0.0` -> `/app/ProjectName/x64/libleptonica-1.82.0.so`  
`/usr/lib/libtesseract.so.5.0.3` -> `/app/ProjectName/x64/libtesseract50.so`  
