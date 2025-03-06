---
Description: Attach Browser
---

# Присоединиться к браузеру

Элемент осуществляет подключение к действующему веб-браузеру, позволяя роботу взаимодействовать с веб-приложениями, в том числе интегрироваться с SAP через веб-интерфейс. Выступает в роли контейнера для других элементов Студии, предназначенных для работы с веб-приложениями.

![](../../../resources/activities/basic/browser/browser-attach-activity.png)

Обратите внимание, что элементы, вложенные в контейнер **Присоединиться к браузеру** и присоединенные к нему, требуют наличия расширения браузера. Способы установки расширений описаны [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-rpa-studio-linux/installation/installation-astra/install-astra-deb-packages).

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Браузер**  
1. **Тип браузера** *[LTools.WebBrowser.Model.BowserTypes]* - Опеределяет тип используемого браузера. По умолчанию `IE` - Internet Explorer. Чтобы выбрать другой браузер, щелкните выпадающий список. Доступны значения: IE, Chrome, Firefox, Opera, Edge, Yandex, SAP
1. **Заголовок браузера** *[String]* - Задает заголовок подключаемого браузера (указывается в кавычках ""). По умолчанию установлено `"*"`. Для автоматического добавления заголовка можно использовать кнопку **Выбрать страницу** ![](../../../resources/activities/basic/browser/magic-stick.png) 
1. **URL** *[String]* - Адрес текущей страницы браузера   
1. **Переменная** *[LTools.WebBrowser.BrowserInst]* - Переменная, содержащая ссылку на ранее подключенный браузер (если имеется) 
1. **Освобождать** - Определяет, нужно ли освобождать ссылку на браузер при выходе 
1. **Таймаут\*** *[Int32]* - Максимальное время ожидания завершения процесса (в миллисекундах). По умолчанию `10000` 

**Вывод**   
1. **Переменная** - Переменная для хранения ссылки на подключенный браузер. Впоследствии, при повторном использовании в процессе контейнера **Присоединиться к браузеру**, ее можно указать для более быстрого подключения в свойстве **Браузер > Переменная**


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
