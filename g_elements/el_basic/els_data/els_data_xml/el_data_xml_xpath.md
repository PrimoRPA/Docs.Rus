# Запрос XPath

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (307).png>)

![](<../../../../.gitbook/assets/image (373).png>)

Компонент, осуществляющий поиск в документе XML в соответствии с запросом XPath.

| Свойство                     | Тип                    | Описание                                                                                                                                                                                          |
| ---------------------------- | ---------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Данные (строка)              | String                 | Строка XML                                                                                                                                                                                        |
| Данные (объект)              | System.Xml.XmlDocument | Объект XML '[https://docs.microsoft.com/ru-ru/dotnet/api/system.xml.xmldocument?view=netframework-4.6](https://docs.microsoft.com/ru-ru/dotnet/api/system.xml.xmldocument?view=netframework-4.6)' |
| XPath\*                      | String                 | Запрос XPath (//s:Body/a:Code) '[https://www.w3schools.com/xml/xpath\_syntax.asp](https://www.w3schools.com/xml/xpath\_syntax.asp)'                                                               |
| Переменная (массив объектов) | System.Xml.XmlNodeList | Переменная, получающая результирующие объекты                                                                                                                                                     |
| Переменная (массив строк)    | List\<String>          | Переменная, получающая результирующие значения                                                                                                                                                    |
| Переменная (строка)          | String                 | Переменная, получающая первое результирующее значение                                                                                                                                             |

{% tabs %}
{% tab title="C#" %}
```csharp
System.Xml.XmlDocument ret = new System.Xml.XmlDocument();
et.LoadXml("xml");
System.Xml.XmlNodeList list = ret.SelectNodes(xp, LTools.Data.Helpers.XMLHelper.CreateNamespaceManager(ret));
```
{% endtab %}

{% tab title="Python" %}
```python
ret = System.Xml.XmlDocument()
ret.LoadXml("xml")
list = ret.SelectNodes(xp, LTools.Data.Helpers.XMLHelper.CreateNamespaceManager(ret))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let ret = System.Xml.XmlDocument();
ret.LoadXml("xml");
let list = ret.SelectNodes(xp, LTools.Data.Helpers.XMLHelper.CreateNamespaceManager(ret));
```
{% endtab %}
{% endtabs %}
