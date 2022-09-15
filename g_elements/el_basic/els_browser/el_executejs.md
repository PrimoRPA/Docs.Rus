# Выполнить JS

![](<../../../.gitbook/assets/image (100) (1) (1) (67).png>)

![](<../../../.gitbook/assets/image (407).png>)

Компонент, выполняющий скрипт JS в браузере.

| Свойство  | Тип    | Описание                                           | Пример
| :---------: | :------: | -------------------------------------------------- | -------------------------
| Скрипт\*  | String | Выполняемый скрипт                                 |
| Таймаут\* | Int32  | Предельное время ожидания завершения процесса (мс) |
| Функция   | Boolean | Признак скрипта-функции |
| Аргумент  | String | Аргумент функции |
| Шаблон поиска |    | Шаблон поиска элемента |
| Элемент   | LTools.WebBrowser.Model.IElementInfo | Ссылка на элемент управления |
| Результат | String | Переменная для сохранения результата работы скрипта | result


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
