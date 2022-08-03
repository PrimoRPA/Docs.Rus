# Сохранить вложение

![](<../../../../.gitbook/assets/image (445).png>)



Компонент, производящий сохранение вложения письма.

Свойства

| Свойство     | Тип                                                                     | Описание                           |
| ------------ | ----------------------------------------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                                                  | Путь к файлу (c:\folder\files.ext) |
| Вложение     | [LTools.Office.Model. OMailAttachment](../datatypes/omailattachment.md) | Вложение письма                    |

{% tabs %}
{% tab title="C#" %}
```csharp
app.SaveAttachment(att, "C\\file");
```
{% endtab %}

{% tab title="Python" %}
```python
app.SaveAttachment(att, "C\\file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SaveAttachment(att, "C\\file");
```
{% endtab %}
{% endtabs %}
