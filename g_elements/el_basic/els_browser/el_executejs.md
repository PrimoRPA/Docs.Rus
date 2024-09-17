# Выполнить JS
*Eng: Execute JS*

Элемент запускает JavaScript-код в веб-браузере. Элемент может применяться для изменения содержимого страницы, взаимодействия с данными и эмуляции действий пользователя.

Для надежности рекомендуется использовать элемент в контейнере [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) либо в контейнере [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach). Тип браузера указывается в свойствах выбранного контейнера. 

![Элемент Выполнить JS](<../../../.gitbook/assets/execute-js-in-container.png>)

## Перед началом работы

Убедитесь, что у вас установлено [расширение браузера](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings/plugin-install) Primo RPA extension на базе манифеста V2 — это все версии, которые начинаются с 1.xx, например, 1.66.

:large_orange_diamond:***Важно**. Элемент не поддерживают работу с расширением Primo RPA extension на базе манифеста V3 — версии этого расширения начинаются на 3.xx. Например, 3.63, 3.66, 3.68.*


## Свойства
Символ `*` в названии свойства указывает на обязательность. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа «Процесс»:**

1. **Скрипт\*** *[String]* — скрипт, который следует выполнить. Кавычки внутри строки требуется экранировать. Если скрипт объявляет функцию, то следует придерживаться шаблона: `"function test(a, v, el) { alert(v); return null; }"`, где **v** — это аргумент.
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса, значение указывается в миллисекундах. По умолчанию `10000`.

**Группа «Функция»:**

1. **Функция** *[Boolean]* — определяет, содержит ли скрипт функцию. По умолчанию чекбокс отключен — функция не используется.
1. **Аргумент** *[String]* — работает только с включенным свойством **Функция**. Укажите в этом поле аргумент функции. Аргументом может быть либо конкретное значение (например, `"hello"`), либо строковая переменная. Можно использовать только один аргумент.
1. **Шаблон поиска** — свойство позволяет выбрать элемент управления веб-страницы, на котором нужно применить скрипт. Для быстрого формирования шаблона рекомендуется использовать инструмент **Волшебная палочка**. Подробнее о шаблоне поиска можно узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns). 

    ![](<../../../.gitbook/assets/execute-js-selector.png>) 

1. **Элемент** *[LTools.WebBrowser.Model.IElementInfo]* — в этом свойстве можно указать переменную, содержащую ссылку на веб-элемент управления.
  
   Как ее получить:
   * В сценарии сначала используем компонент [**Присутствие элемента**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_exists). В этом компоненте, в свойстве вывода **Элемент**, указываем переменную с типом [UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/datatypes/uicontrol) — она сохранит ссылку на найденный элемент управления.
   * В элементе **Выполнить JS**, в свойстве **Элемент**, открываем редактор кода и указываем `<название переменной>.BrowserElement`.
  
     ![](<../../../.gitbook/assets/execute-js-browser-element.png>)                                                                  

**Группа «Вывод»:**

* **Результат** *[String]* — название переменной, в которую будет сохранен результат работы скрипта.     

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
