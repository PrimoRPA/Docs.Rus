# Присоединиться к браузеру
*Eng: Attach Browser*

Элемент осуществляет подключение к действующему веб-браузеру, позволяя роботу взаимодействовать с веб-приложениями, в том числе интегрироваться с SAP через веб-интерфейс. Выступает в роли контейнера для других элементов Студии, предназначенных для работы с веб-приложениями.

![](<../../../.gitbook/assets/image (403).png>)

Обратите внимание, что элементы, вложенные в контейнер **Присоединиться к браузеру** и присоединенные к нему, требуют наличия расширения браузера. Способы установки расширений описаны [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install).

**Кроссплатформенность:** работает с Windows, Linux, MacOS.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство           | Тип                                 | Описание                                                                                        |
| ------------------ | ----------------------------------- | ----------------------------------------------------------------------------------------------- |
| Тип браузера       | LTools.WebBrowser.Model.BowserTypes | Опеределяет тип используемого браузера. По умолчанию `IE` - Internet Explorer. Чтобы выбрать другой браузер, щелкните выпадающий список. Доступны значения: IE, Chrome, Firefox, Opera, Edge, Yandex, SAP |
| Заголовок браузера | String                              | Задает заголовок подключаемого браузера (указывается в кавычках "")        
| Освобождать        |                                     | Освободить ресурсы браузера
| Переменная         | LTools.WebBrowser.BrowserInst       | Переменная, для хранения ссылки на подключенный браузер                                           |
| Таймаут\*          | Int32                               | Максимальное время ожидания завершения процесса (в миллисекундах)                                              |
| URL                | String                              | Адрес (URL) текущей страницы браузера
|**SAP**             |                                     | 
| Id компонента      | String                              | Идентификатор компонента в системе SAP
| Компонент          | LTools.SAP.Model.SAPUIItem          | Специфический элемент или объект в SAP
**Вывод**
| Переменная         |                                     | Результат, возвращаемый после выполнения операции


## Пример на Learning

Пример процесса с использованием данного элемента доступен [Learning](https://github.com/PrimoRPA/Learning/tree/master). Скачайте проект StudioActivities, откройте его в Студии и выберите процесс `StudioActivities/Ru/Браузер/Присоединиться к браузеру.ltw` для просмотра.



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
