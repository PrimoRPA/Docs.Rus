# HTML к объекту

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (249).png>)

![](<../../../../.gitbook/assets/image (381).png>)

Компонент, осуществляющий преобразование HTML в объект и поиск в нем. Если указан XPath, результат будет иметь тип AngleSharp.Dom.INode, в противном случае AngleSharp.Html.Parser.IHtmlDocument

| Свойство     | Тип                                                         | Описание                                                                                                                       |
| ------------ | ----------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| Переменная\* | AngleSharp.Dom.INode / AngleSharp.Html.Parser.IHtmlDocument | Переменная, получающая результат поиска '[https://github.com/AngleSharp/AngleSharp](https://github.com/AngleSharp/AngleSharp)' |
| Данные\*     | String                                                      | Строка HTML                                                                                                                    |
| XPath        | String                                                      | Строка выражения XPath '[https://ru.wikipedia.org/wiki/XPath](https://ru.wikipedia.org/wiki/XPath)'                            |

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
