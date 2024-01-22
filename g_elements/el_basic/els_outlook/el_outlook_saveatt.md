---
description: Save attachment
---


# Сохранить вложение

![](<../../../.gitbook/assets/image (554).png>)

Элемент сохраняет вложение письма.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип                                                                               | Описание                           |
| ------------ | --------------------------------------------------------------------------------- | ---------------------------------- |
| Путь к файлу | String                                                                            | Путь к файлу. Пример: `"C:\\folder\\files.ext"` |
| Вложение     | [LTools.Office.Model.OMailAttachment](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailattachment) | Название переменной, хранящей вложение письма   |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
app.SaveAttachment(att, "C:\\file.txt");
```
{% endtab %}

{% tab title="Python" %}
```python
app.SaveAttachment(att, "C:\\file.txt")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SaveAttachment(att, "C:\\file.txt");
```
{% endtab %}
{% endtabs %}
