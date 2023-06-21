# Клик текста мышью

![](<../../../.gitbook/assets/image (416).png>)

Компонент, производящий клик мышью на заданном тексте.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип                | Описание                                           |
| --------------- | ------------------ | -------------------------------------------------- |
| ***Настройки OCR*** | | |
| Переменная\*    | LTools.OCR.OCRInst | Переменная со ссылкой на ядро OCR                  |
| ***Процесс*** | | |
| Искомый текст\* | String             | Искомый текст                                      |
| Кнопка мыши\*   | -                  | Кнопка мыши для клика. По умолчанию INVOKE. <p>Доступные значения: BUTTON_LEFT - одинарный щелчок левой кнопкой, BUTTON_LEFT_DOUBLECLICK - дважды левой кнопкой, BUTTON_RIGHT - одинарный щелчок правой кнопкой, BUTTON_MIDDLE - колесико</p> |
| Индекс          | Int32              | Индекс вхождения искомого текста - при нахождении нескольких строк, попадающих под условие поиска, позволяет указать индекс нужной строки для клика. По умолчанию `0` |
| Таймаут\*       | Int32              | Предельное время ожидания завершения процесса (мс). По умолчанию `10000` |
| ***OCR*** | | |
| Смещение X      | Int32              | Процент смещения по оси X относительно центра      |
| Смещение Y      | Int32              | Процент смещения по оси Y относительно центра      |

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
app.ClickText("text", 10000, 0, 0, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU")
app.ClickText("text", 10000, 0, 0, LTools.Desktop.Model.MouseButtons.BUTTON_LEFT)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
app.ClickText("text", 10000, 0, 0, _lib.LTools.Desktop.Model.MouseButtons.BUTTON_LEFT);
```
{% endtab %}
{% endtabs %}

