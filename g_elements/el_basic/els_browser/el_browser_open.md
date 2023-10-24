# Открыть браузер

*Eng: Open browser*

Элемент выполняет 2 основные функции:
1. Открывает новый экземпляр браузера либо новую вкладку в уже открытом браузере. Исключение - Internet Explorer. Для него всегда будет открываться только новый экземпляр.
2. Выступает в роли контейнера для других элементов, работающих с веб-страницами. Например, для таких, как [**Присутствие элемента**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_exists), [**Клик мышью**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_click), [**Обновить страницу**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_refresh) и т. д.

   Пример:

   ![](<../../../.gitbook/assets/open-browser-as-container-new.png>)

   Элементы, вложенные в контейнер **Открыть браузер** и присоединенные к нему, требуют наличия расширения браузера, хотя сам контейнер работает независимо от него. Способы установки расширений описаны [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install).

**Кроссплатформенность:** работает с Windows, Linux, MacOS.
   
## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа «Браузер»**:

1. **URL**. String. Адрес страницы. Пример: `"https://primo-rpa.ru/"`.
2. **Тип браузера**. Тип используемого браузера. По умолчанию `IE` - Internet Explorer. Чтобы выбрать другое значение, кликните выпадающий список:

   ![](<../../../.gitbook/assets/open-browser-type-browser.png>)

   Значения, которые начинаются со слов `Web Driver`, предназначены для тех случаев, когда необходимо использовать Selenium WebDriver. По умолчанию веб-драйвер уже встроен в Студию, но для успешной работы версии драйвера и браузера должны совпадать. Если они не совпадают, то веб-драйвер требуется обновить.
   
4. **Освобождать**. Boolean. Определите, следует ли освобождать ссылку на браузер при выходе. По умолчанию чекбокс выключен - ссылка не освобождается. 
5. **Скрывать**. Boolean. Только при совместном использовании с WebDriver, кроме Edge. Определите, следует ли запускать браузер невидимым для пользователя - он будет работать в фоне. По умолчанию чекбокс выключен. 
 
**Группа «Вывод»**:

**Переменная**. LTools.WebBrowser.BrowserInst. Здесь можно указать переменную для сохранения ссылки на подключенный браузер. 

### Если браузер не открылся

Если использование элемента не привело к ожидаемому результату, проверьте:

- установлен в системе браузер, выбранный в свойстве **Тип браузера**;
- права доступа пользователя на использование браузера;
- описание ошибки в консоли.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Open(wf, LTools.WebBrowser.Model.BrowserTypes.IE)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Open(wf, _lib.LTools.WebBrowser.Model.BrowserTypes.IE);
```
{% endtab %}
{% endtabs %}




