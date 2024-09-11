# Клик изображения мышью

![](<../../../.gitbook/assets/image (449).png>)

Элемент производит клик мышью на изображении. Изображение указывается в свойствах элемента. В случае, если искомое изображение не указано, растр будет взят из скриншота элемента.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство            | Тип                                | Описание                                           |
| ------------------- | ---------------------------------- | -------------------------------------------------- |
| Искомое изображение | [System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8) | Растр искомого изображения                         |
| Точность            | [Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)                 | Точность совпадения растра (% от 0 до 1)           |
| Смещение X          | Int32                              | Процент смещения по оси X относительно центра     |
| Смещение Y          | Int32                              | Процент смещения по оси Y относительно центра     |
| Область             |                                    | Область поиска компонента                          |
| Позиция             |                                    | Позиция курсора при клике                          |
| Кнопка мыши\*       | LTools.Desktop.Model. MouseButtons | Кнопка мыши                                        |
| Кнопка клавиатуры   |                                    | Кнопка клавиатуры                                  |
| Активировать        | Boolean                            | Активировать окно перед кликом                     |
| Таймаут\*           | Int32                              | Предельное время ожидания завершения процесса (мс) |


## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Откройте процесс `Клик изображения мышью.ltw`.


## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp.Click(wf, (System.Drawing.Bitmap)System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000, 0, 0, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.OCR.OcrApp.Click(wf, System.Drawing.Bitmap.FromFile("Файл 1"), 0.9, 10000, 0, 0, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var bmp = host.newObj(_lib.System.Drawing.Bitmap, "Файл 1");
_lib.LTools.OCR.OcrApp.Click(wf, bmp, 0.9, 10000, 0, 0, _lib.LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
```
{% endtab %}
{% endtabs %}
