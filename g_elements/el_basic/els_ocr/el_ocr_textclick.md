# Клик текста мышью

![](<../../../.gitbook/assets/image (416).png>)

Компонент, производящий клик мышью на заданном тексте.

| Свойство        | Тип                | Описание                                           |
| --------------- | ------------------ | -------------------------------------------------- |
| Переменная\*    | LTools.OCR.OCRInst | Переменная со ссылкой на ядро OCR                  |
| Искомый текст\* | String             | Искомый текст                                      |
| Смещение X      | Int32              | Процент смещения по оси X относительно центра      |
| Смещение Y      | Int32              | Процент смещения по оси Y относительно центра      |
| Таймаут\*       | Int32              | Предельное время ожидания завершения процесса (мс) |

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

