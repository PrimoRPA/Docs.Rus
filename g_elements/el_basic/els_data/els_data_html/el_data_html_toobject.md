# HTML к объекту

*Eng: HTML to object*


![](<../../../../.gitbook/assets/image (381).png>)


Этот компонент предназначен для преобразования HTML-кода в объект и выполнения поиска в этом объекте. В зависимости от наличия или отсутствия указания XPath, результат работы компонента будет различаться:

- Если **XPath** указан, результат будет представлен в виде объекта типа `AngleSharp.Dom.INode`.
- Если **XPath** не указан, результат будет объектом типа `AngleSharp.Html.Parser.IHtmlDocument`.

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                                                         | Описание                                                                                                                       |
|--------------|-------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------|
| Переменная\* | AngleSharp.Dom.INode / AngleSharp.Html.Parser.IHtmlDocument | Переменная для хранения результата поиска. Информация о библиотеке доступна на [AngleSharp GitHub](https://github.com/AngleSharp/AngleSharp). |
| Данные\*     | String                                                      | Строка с HTML-кодом для преобразования и анализа.                                                                              |
| XPath        | String                                                      | Строка с выражением XPath для поиска в HTML-документе. Дополнительная информация об XPath доступна на [Wikipedia](https://ru.wikipedia.org/wiki/XPath). |


##  Learning

Для изучения работы с элементом **HTML к объекту**, вы можете скачать обучающий RPA-проект по следующей ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip)

1. Скачайте архив с обучающими материалами с указанной страницы.
2. Распакуйте архив и откройте проект `StudioActivities` в вашей среде разработки.
3. Найдите процесс `StudioActivities/Ru/Данные/HTML/HTML к объекту.ltw` для изучения работы элемента.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
List<AngleSharp.Dom.INode> ret = AngleSharp.XPath.Extensions.SelectNodes(new AngleSharp.Html.Parser.HtmlParser().ParseDocument("html").DocumentElement, "xpath");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = AngleSharp.XPath.Extensions.SelectNodes(AngleSharp.Html.Parser.HtmlParser().ParseDocument("html").DocumentElement, "xpath")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var doc = host.newObj(_lib.AngleSharp.Html.Parser.HtmlParser);
var ret = _lib.AngleSharp.XPath.Extensions.SelectNodes(doc.ParseDocument("html").DocumentElement, "xpath");
```
{% endtab %}
{% endtabs %}
