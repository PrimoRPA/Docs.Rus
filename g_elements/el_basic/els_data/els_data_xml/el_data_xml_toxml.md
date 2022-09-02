# Объект к XML

![](<../../../../.gitbook/assets/image (100) (1) (237).png>)

![](<../../../../.gitbook/assets/image (390).png>)

Компонент, осуществляющий объекта в строку XML.

| Свойство     | Тип    | Описание                                         |
| ------------ | ------ | ------------------------------------------------ |
| Переменная\* | String | Переменная, получающая результирующую строку XML |
| Данные\*     | Object | Исходный объект                                  |

{% tabs %}
{% tab title="C#" %}
```csharp
System.Xml.XmlSerializer xsSubmit = new System.Xml.XmlSerializer(xml.GetType());
var xmlstr = "xml";
using (var sww = new StringWriter())
{
    using (System.Xml.XmlWriter writer = System.Xml.XmlWriter.Create(sww))
    {
        xsSubmit.Serialize(writer, xml);
        xmlstr = sww.ToString(); 
    }
}
```
{% endtab %}

{% tab title="Python" %}
```python
xsSubmit = System.Xml.XmlSerializer(obj.GetType())
sww = StringWriter()
writer = System.Xml.XmlWriter.Create(sww)
xsSubmit.Serialize(writer, xml);
xmlstr = sww.ToString()
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let xsSubmit = _lib.System.Xml.XmlSerializer(obj.GetType());
let sww = StringWriter();
let writer = _lib.System.Xml.XmlWriter.Create(sww);
xsSubmit.Serialize(writer, xml);
let xmlstr = sww.ToString();
```
{% endtab %}
{% endtabs %}
