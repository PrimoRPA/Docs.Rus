# Присоединиться к браузеру

Элемент осуществляет подключение к действующему браузеру.

![](<../../../.gitbook/assets/image (403).png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство           | Тип                                 | Описание                                                                                        |
| ------------------ | ----------------------------------- | ----------------------------------------------------------------------------------------------- |
| Тип браузера       | LTools.WebBrowser.Model.BowserTypes | Тип используемого браузера. По умолчанию `IE` - Internet Explorer. Чтобы выбрать другой браузер, щелкните выпадающий список. Доступны значения: IE, Chrome, Firefox, Opera, Edge, Yandex, SAP |
| Заголовок браузера | String                              | Заголовок подключаемого браузера                                                                |
| Переменная         | LTools.WebBrowser.BrowserInst       | Переменная, содержащая ссылку на подключенный браузер                                           |
| Таймаут\*          | Int32                               | Предельное время ожидания завершения процесса (мс)                                              |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
```
{% endtab %}
{% endtabs %}
