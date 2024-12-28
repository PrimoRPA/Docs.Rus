# Выполнить JS
*Eng: Execute JS*

Элемент запускает JavaScript-код в веб-браузере. Элемент может применяться для изменения содержимого страницы, взаимодействия с данными и эмуляции действий пользователя.

Для надежности рекомендуется использовать элемент в контейнере [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) либо в контейнере [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach). Тип браузера указывается в свойствах выбранного контейнера. 

![Элемент Выполнить JS](<../../../.gitbook/assets/execute-js-in-container.png>)

## Перед началом работы

Убедитесь, что у вас установлено [расширение браузера](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install) Primo RPA extension. 

> Начиная с версии 25.1, активность 'Выполнить запрос' (ExecuteJS) в расширениях, использующих Manifest V3, была адаптирована к новым требованиям политик безопасности Chromium. Для обеспечения корректной работы и возможности добавления пользовательского скрипта, перед его выполнением активность теперь автоматически перезагружает страницу. Этот механизм необходим для интеграции пользовательских скриптов в соответствии с ограничениями Manifest V3. 


## Свойства
Символ `*` в названии свойства указывает на обязательность. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


**Группа «Вывод»:**
* **Результат** *[String]* — название переменной, в которую будет сохранен результат работы скрипта. 

**Группа «Процесс»:**
1. **Скрипт\*** *[String]* — скрипт, который следует выполнить. Кавычки внутри строки требуется экранировать. Если скрипт объявляет функцию, то следует придерживаться шаблона: `"function test(a, v, el) { alert(v); return null; }"`, где **v** — это аргумент.
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса, значение указывается в миллисекундах. По умолчанию `10000`.

**Группа «Функция»:**
1. **Функция** *[Boolean]* — определяет, содержит ли скрипт функцию. По умолчанию чекбокс отключен — функция не используется.
1. **Аргумент** *[String]* — работает только с включенным свойством **Функция**. Укажите в этом поле аргумент функции. Аргументом может быть либо конкретное значение (например, `"hello"`), либо строковая переменная. Можно использовать только один аргумент.
1. **Шаблон поиска** — свойство позволяет выбрать элемент управления веб-страницы, на котором нужно применить скрипт. Для быстрого формирования шаблона рекомендуется использовать инструмент **Волшебная палочка**. Подробнее о шаблоне поиска можно узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns). 

    ![Иконка волшебной палочки](<../../../.gitbook/assets/execute-js-selector.png>) 

1. **Элемент** *[LTools.WebBrowser.Model.IElementInfo]* — в этом свойстве можно указать переменную, содержащую ссылку на веб-элемент управления.
  
   Как ее получить:
   * В сценарии сначала используем компонент [**Присутствие элемента**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_exists). В этом компоненте, в свойстве вывода **Элемент**, указываем переменную с типом [UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/datatypes/uicontrol) — она сохранит ссылку на найденный элемент управления.
   * В элементе **Выполнить JS**, в свойстве **Элемент**, открываем редактор кода и указываем `<название переменной>.BrowserElement`.
  
     ![Как открыть редактор кода](<../../../.gitbook/assets/execute-js-browser-element.png>)                                                                  


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Eval("script", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
app.Eval("script", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Test page*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
app.Eval("script", 10000);
```
{% endtab %}
{% endtabs %} 
