# Клик изображения мышью

![](<../../../.gitbook/assets/image (449).png>)

Элемент производит клик мышью на изображении. Искомое изображение указывается в свойствах элемента. В случае, если искомое изображение не указано, растр будет взят из скриншота элемента.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**OCR**:

1. **Искомое изображение** *[[System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8)]* — растр искомого изображения. Если значение не указано, растр будет взят из скриншота элемента.           
1. **Область** — область поиска компонента. Пример: `0; 0; 0; 0`, где значения слева направо: высота (height), слева (left), сверху (top), ширина (width).
1. **Точность** *[[Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)]* — точность совпадения растра (% от 0 до 1).
1. **Смещение X** *[Int32]* — процент смещения по оси X относительно центра.     
1. **Смещение Y** *[Int32]* — процент смещения по оси Y относительно центра.
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса (мс). По умолчанию `10000`.

**Процесс**:

1. **Позиция** — позиция курсора при клике. По умолчанию `Center`. Чтобы выбрать другое значение, нажмите выпадающий список.   
1. **Кнопка мыши\*** *[LTools.Desktop.Model.MouseButtons]* — кнопка мыши. Нажмите выпадающий список, чтобы выбрать доступное значение:
   * INVOKE — значение по умолчанию. Одиночный клик левой кнопкой мыши — программный клик через Win32, при нем не наводится курсор, и окно приложения может быть свернутым. Однако нужно иметь в виду, что существуют приложения, не поддерживающие программный клик.
   * BUTTON_LEFT — одиночный клик левой кнопкой.
   * BUTTON_LEFT_DOUBLECLICK — двойной клик левой кнопкой.
   * BUTTON_RIGHT — одиночный клик правой кнопкой.
   * BUTTON_MIDDLE — колесико.                                       
1. **Кнопка клавиатуры** — кнопка клавиатуры. По умолчанию не задана — `NONE`. Доступные значения:
   * CTRL
   * ALT
   * SHIFT                
1. **Активировать** *[Boolean]* — определяет, следует ли активировать окно перед кликом. Если галочка установлена, окно будет активировано.               



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
