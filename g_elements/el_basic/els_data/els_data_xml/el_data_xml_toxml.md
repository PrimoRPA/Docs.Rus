# Объект к XML

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (134).png>)

![](<../../../../.gitbook/assets/image (390).png>)

Компонент осуществляет преобразование объекта в строку XML.

## Свойства

Все свойства элемента разделены на группы - они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство     | Тип    | Описание                                         |
| ------------ | ------ | ------------------------------------------------ |
| ***Общие***  | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Обработка***  | |  |
| Данные\*      | Object | Укажите исходный объект                         |
| ***Вывод***   | |  |
| Переменная\* | String | Переменная, получающая результирующую строку XML |
| Форматировать | Boolean | Определите, нужно ли форматировать строку XML, добавив отступы для комфортного чтения. Если галочка установлена, XML отформатируется. Если нет, то данные будут отображаться в одну XML-строку |

## Только код
Пример использования элемента в процессе с типом **Только код (Only code)**:

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
