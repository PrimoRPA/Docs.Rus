---
description: Save message (IMAP)
---

# Сохранить сообщение (IMAP)


Элемент позволяет сохранять сообщения электронной почты на диск в формате EML. 


![](<../../../.gitbook/assets1/savemsg.png>)


### Свойства

Символ * в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство              | Тип                          | Описание                                           |
| --------------------- | ---------------------------- | -------------------------------------------------- |
|**Сервер** |  |
| Путь*           | String                       | Путь, по которому будет сохранён файл.            |
| Сообщение*        | LTools.Network.Model.EMail.MailMessage | Сообщение электронной почты для сохранения.         |


### Свойства объекта LTools.Network.Model.EMail.MailMessage

| Свойство              | Тип                          | Описание                                           |
| --------------------- | ---------------------------- | -------------------------------------------------- |
| *UID*               | String                       | Уникальный идентификатор сообщения.                |
| *Subject*           | String                       | Тема сообщения.                                    |
| *From*              | List<String>                 | Список отправителей сообщения.                     |
| *To*                | List<String>                 | Список получателей сообщения.                      |
| *CC*                | List<String>                 | Список получателей в копии.                        |
| *Date*              | DateTime?                    | Дата отправки сообщения.                           |
| *TextBody*          | String                       | Текстовое тело сообщения.                          |
| *HtmlBody*          | String                       | HTML тело сообщения.                               |
| *Attachments*       | List<MailAttachment>         | Список вложений сообщения.                         |



## Только код

Пример использования элемента в процессе с типом Только код (Pure code)

{% tabs %}
{% tab title="C#" %}
```csharp
var app = new LTools.Office.OutlookApp();
var msg = new LTools.Office.Model.OMailMessage();
string file = "C:\\path\\to\\save\\message.eml";
// Сохранение сообщения в формате EML
app.SaveMessage(msg, file, "EML");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp()
msg = LTools.Office.Model.OMailMessage()
file = "C:\\path\\to\\save\\message.eml"
// Сохранение сообщения в формате EML
app.SaveMessage(msg, file, "EML")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = new _lib.LTools.Office.OutlookApp();
var msg = new _lib.LTools.Office.Model.OMailMessage();
var file = "C:\\path\\to\\save\\message.eml";
// Сохранение сообщения в формате EML
app.SaveMessage(msg, file, "EML");
```
{% endtab %}
{% endtabs %}



