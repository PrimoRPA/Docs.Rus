---
description: Image vanish
---

# Исчезновение изображения

![](<../../../.gitbook/assets/image (423).png>)

Элемент ожидает исчезновения искомого изображения на экране. В случае, если искомое изображение не указано, растр будет взят из [скриншота элемента](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio/process/elements#rabota-so-skrinshotami-vnutri-elementa).

## Свойства

Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Искомое изображение** *[[System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8)]* — название переменной, которая содержит растр искомого изображения. 
1. **Точность** *[[Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-6.0)]* — точность совпадения растра (% от 0 до 1). По умолчанию `0.9`.
1. **Таймаут\*** *[Int32}* — предельное время ожидания завершения процесса (мс). По умолчанию `10000`.


## Пример использования

RPA-проект с демонстрацией работы элемента можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив, после чего откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Исчезновение изображения.ltw` в соответствующей папке проекта. 


## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp.Vanish(wf, (System.Drawing.Bitmap)System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.OCR.OcrApp.Vanish(wf, System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.OCR.OcrApp.Vanish(wf, _lib.System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000);
```
{% endtab %}
{% endtabs %}
