# Требования к изображениям для инфреренса

Для успешного распознавания изображений на стадии инференса соблюдайте следующие требования.

### Общие требования

1. **Форматы:** JPEG, JPG, JPE, PNG, PDF, BMP, TIF, TIFF, DIB.
2. **Разрешение и качество изображений**:
   - Разрешение должно быть не менее 100 DPI\*. Допустимый диапазон 100-300 DPI, где 300 DPI является рекомендуемым значением при реальном размере изображения.
   - Избегайте изображений с размытостью, слишком темные и слишком светлые изображения.
   - Скан-копии всегда предпочтительнее фотографий, так как не содержат геометрических искажений. Это особенно важно для таблиц.


### Пример

Узнать DPI для файла .jpg можно, посмотрев свойства изображения:

![Пример DPI для фото СНИЛС](<../../../../.gitbook/assets1/primo-ai/how-know-dpi.png>)

Поскольку DPI нет в формате PNG, то воспользуемся следующей формулой для расчета: 
* если размер документа — 1 дюйм х 1 дюйм, то разрешение его скана должно быть не менее 100 х 100 пикселей. 

Например:
* Минимальное разрешение для документа формата А4 — 1170 х 830 пикселей, поскольку его размер 11.7 x 8.3 дюймов. 
* Минимальное разрешение для паспорта — 1000 х 700 пикселей, поскольку его физический размер меньше. Но если скан паспорта сделан на фоне А4, без обрезки пустого места, то — 1170 х 830, а лучше — 2340 х 1660 пикселей.


> \**DPI — количество точек (пикселей) на дюйм. Дюйм - единица длины равная 2,541 см или 25.4 мм.*


### См. также
- [Требования к изображениям для обучения](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-ai-server/user/smart-ocr/requirements/dataset-requirements)

