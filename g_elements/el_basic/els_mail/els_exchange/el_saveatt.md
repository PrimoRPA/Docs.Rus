# Сохранить вложение

*Eng: Save attachment*

Элемент позволяет сохранить вложение письма.

![](<../../../../.gitbook/assets/image (773).png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                                                                     | Описание                           |
| ------------ | ----------------------------------------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                                                  | Путь к файлу (c:\folder\files.ext) |
| Вложение     | [LTools.Office.Model. OMailAttachment](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailattachment) | Вложение письма. Например, фото, документ, а с версии 23.11 и другое письмо (в виде файла \*.eml) |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
