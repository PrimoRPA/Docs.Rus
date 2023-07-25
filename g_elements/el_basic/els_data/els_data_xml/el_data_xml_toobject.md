# XML к объекту

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (52).png>)

![](<../../../../.gitbook/assets/image (248).png>)

Компонент, осуществляющий преобразование XML в объект.

| Свойство     | Тип                    | Описание                                                                                                                                                                                                                            |
| ------------ | ---------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Переменная\* | System.Xml.XmlDocument | Переменная, получающая результирующий объект '[https://docs.microsoft.com/ru-ru/dotnet/api/system.xml.xmldocument?view=netframework-4.6](https://docs.microsoft.com/ru-ru/dotnet/api/system.xml.xmldocument?view=netframework-4.6)' |
| Данные\*     | String                 | Строка XML                                                                                                                                                                                                                          |

{% tabs %}
{% tab title="C#" %}
```csharp
System.Xml.XmlDocument ret = System.Xml.XmlDocument().LoadXml(xml);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = System.Xml.XmlDocument().LoadXml(xml)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let ret = System.Xml.XmlDocument().LoadXml(xml);
```
{% endtab %}
{% endtabs %}
