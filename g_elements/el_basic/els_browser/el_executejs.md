# Выполнить JS
*Eng: Execute JS*

Элемент позволяет запускать JavaScript-код в веб-браузере. Может пригодиться для изменения содержимого страницы, взаимодействия с данными и эмуляции действий пользователя.

Для надежности рекомендуется использовать элемент в контейнере [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) либо [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach). Тип браузера указывается в контейнере.

![](<../../../.gitbook/assets/execute-js-in-container.png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа «Процесс»:**

1. **Скрипт\***. String. Введите скрипт, который нужно выполнить. Помните, что кавычки внутри строки нужно экранировать. Если скрипт объявляет функцию, то следует придерживаться шаблона: `"function test(a, v, el) { alert(v); return null; }"`. Где v - это аргумент.
2. **Таймаут\***. Int32. Предельное время ожидания завершения процесса в миллисекундах. По умолчанию `10000`.

**Группа «Функция»:**

1. **Функция**. Boolean. Установите чекбокс, если скрипт содержит функцию. По умолчанию не используется.
2. **Аргумент**. String. Работает только с включенным свойством **Функция**. Укажите в этом поле аргумент функции. Аргументом может быть либо конкретное значение (например, `"hello"`), либо строковая переменная. Можно использовать только один аргумент.
3. **Шаблон поиска**. Позволяет выбрать элемент управления веб-страницы, на котором нужно отработать скрипт. Для быстрого формирования шаблона рекомендуется использовать инструмент **Волшебная палочка**. Подробнее о шаблоне поиска можно узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/searchpatterns). 

    ![](<../../../.gitbook/assets/execute-js-selector.png>) 

4. **Элемент**. LTools.WebBrowser.Model.IElementInfo. В этом свойстве можно указать переменную, содержащую ссылку на веб-элемент управления.
  
   Как ее получить:
   * В сценарии сначала используем компонент [**Присутствие элемента**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_exists). В этом компоненте, в свойстве вывода **Элемент**, указываем переменную с типом [UIControl](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/datatypes/uicontrol) - она сохранит ссылку на найденный элемент управления.
   * В элементе **Выполнить JS**, в свойстве **Элемент**, открываем редактор кода и указываем `<название переменной>.BrowserElement`.
  
     ![](<../../../.gitbook/assets/execute-js-browser-element.png>)                                                                  

**Группа «Вывод»:**
1. **Результат**. String. Переменная для сохранения результата работы скрипта.     

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
