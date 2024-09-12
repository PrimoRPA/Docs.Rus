---
description: Image exists
---

# Поиск изображения

![](<../../../.gitbook/assets/image (384).png>)

Элемент производит поиск заданного изображения на экране. Если искомое изображение не указано, то растр будет взят из [скриншота элемента](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/process/elements#rabota-so-skrinshotami-vnutri-elementa).

## Свойства

Символ `*` в названии указывает на обязательность заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**OCR**

1. **Искомое изображение** *[[System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8)]* — растр искомого изображения.
1. **Точность** *[[Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)]* — точность совпадения растра (% от 0 до 1). По умолчанию `0.9`.
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса (мс). По умолчанию `10000`.


**Вывод**

1. **Координаты** *[[System.Drawing.Rectangle](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.rectangle?view=netcore-3.0)]* — название переменной, в которую сохранятся координаты найденного изображения.
1. **Результат** *[Boolean]* — название переменной, в которую сохранится результат поиска:
   * `true` — изображение найдено.
   * `false` — изображение не найдено.
1. **Создавать исключение** *[Boolean]* — определяет, следует ли создавать исключение, если изображение не нашлось. По умолчанию параметр включен, исключение будет создаваться.


## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Поиск изображения.ltw` в соответствующей папке проекта.



## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код (Pure code)**:

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
