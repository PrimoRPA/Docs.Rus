# Клик изображения мышью

![](../../.gitbook/assets1/studio-linux-elements-basic/ocr-mouse-click.PNG)

Компонент, производящий клик мышью на заданном изображении.

В случае, если значение Искомого изображения не указано, растр берется из скриншота компонента.

## Свойства
Символ `*` в названии свойства указывает на обязательность. 
Описание общих свойств элемента см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Процесс**
1. **Позиция** - Позиция курсора при клике.
1. **Кнопка мыши\*** *[LTools.Desktop.Model. MouseButtons]* - Кнопка мыши.
1. **Кнопка клавиатуры** - Кнопка клавиатуры.

**OCR**
1. **Искомое изображение** *[[SixLabors.ImageSharp.Image](https://docs.sixlabors.com/api/ImageSharp/SixLabors.ImageSharp.Image.html)]* - Растр искомого изображения.
1. **Точность** *[[Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)]* - Точность совпадения растра (% от 0 до 1).
1. **Ядро** *[Open/External]* - Тип ядра разбора.
1. **Смещение X** *[Int32]* - Процент смещения по оси X относительно центра.
1. **Смещение Y** *[Int32]* - Процент смещения по оси Y относительно центра.
1. **Таймаут\*** *[Int32]* - Предельное время ожидания завершения процесса (мс).

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
