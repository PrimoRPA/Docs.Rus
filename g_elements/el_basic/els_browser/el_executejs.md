# Выполнить JS

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (79).png>)

![](<../../../.gitbook/assets/image (407).png>)

Компонент, выполняющий скрипт JS в браузере.

|    Свойство   |                  Тип                 | Описание                                            |
| :-----------: | :----------------------------------: | --------------------------------------------------- |
| ***Процесс***    |  |                        |
|    Скрипт\*   |                String                | Введите скрипт, который нужно выполнить. Помните, что кавычки внутри строки нужно экранировать. Есди скрипт объявляет функцию, то следует придерживаться шаблона: "function test(a, v, el) { alert(v); return null; }"             |
|   Таймаут\*   |                 Int32                | Предельное время ожидания завершения процесса (мс)  |
| ***Функция***    |  |                        |
|    Функция    |                Boolean               | Установите флаг, если скрипт содержит функцию        |
|    Аргумент   |                String                | Работает совместно с флагом **Функция**. Укажите в этом поле аргумент функции. Аргументом может быть либо конкретное значение (например, "hello"), либо переменная. Можно использовать только один аргумент |
| Шаблон поиска |                                      | Шаблон поиска позволяет выбрать элемент сайта, на котором нужно отработать скрипт |
|    Элемент    | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления                        |
| ***Вывод***    |  |                        |
|   Результат   |                String                | Укажите переменную для сохранения результата работы скрипта |

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
