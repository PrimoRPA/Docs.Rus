# Microsoft OCR

![](<../../../.gitbook/assets/image (263).png>)

Компонент, осуществляющий подключение к ядру OCR Microsoft (только Windows 10).

Для установки языковых пакетов необходимо проделать следующие процедуры:

1. &#x20;Нажмите кнопку **Пуск**, а затем выберите **Параметры** > **Время и язык** > **Язык**.
2. Нажмите кнопку  **Добавить язык**.
3. Выберите нужный Вам язык из списка и нажмите **Далее**
4. Снимите галку с пункта **Сделать языком по умолчанию** и нажмите **Установить**.

| Свойство   | Тип                | Описание                                     |
| ---------- | ------------------ | -------------------------------------------- |
| Язык\*     | String             | Язык данных нейросети (en-US)                |
| Переменная | LTools.OCR.OCRInst | Переменная для сохранения ссылки на ядро OCR |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.OCR.OcrApp app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.OCR.OcrApp.InitMicrosoft(wf, "ru-RU");
```
{% endtab %}
{% endtabs %}

