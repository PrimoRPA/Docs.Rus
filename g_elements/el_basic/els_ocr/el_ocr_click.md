# Клик изображения мышью

![](<../../../.gitbook/assets/image (449).png>)

Компонент, производящий клик мышью на заданном изображении.

В случае, если значение Искомого изображения не указано, растр берется из скриншота компонента

| Свойство            | Тип                                | Описание                                           |
| ------------------- | ---------------------------------- | -------------------------------------------------- |
| Искомое изображение | [System.Drawing.Bitmap](https://learn.microsoft.com/ru-ru/dotnet/api/system.drawing.bitmap?redirectedfrom=MSDN&view=netframework-4.8)              | Растр искомого изображения                         |
| Точность            | [Double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)                             | Точность совпадения растра (% от 0 до 1)           |
| Смещение X          | Int32                              |  Процент смещения по оси X относительно центра     |
| Смещение Y          | Int32                              |  Процент смещения по оси Y относительно центра     |
| Область             |                                    | Область поиска компонента                          |
| Позиция             |                                    | Позиция курсора при клике                          |
| Кнопка мыши\*       | LTools.Desktop.Model. MouseButtons | Кнопка мыши                                        |
| Кнопка клавиатуры   |                                    | Кнопка клавиатуры                                  |
| Активировать        | Boolean                            | Активировать окно перед кликом                     |
| Таймаут\*           | Int32                              | Предельное время ожидания завершения процесса (мс) |

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
