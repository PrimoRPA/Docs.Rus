---
description: Send message
---

# Отправить сообщение



Элемент выполняет отправку электронного письма через Outlook. Размещается внутри контейнера [**Приложение Outlook**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook).

![](<../../../.gitbook/assets1/outlook-send-message.png>)

Применение элемента позволяет достичь следующих целей:
- сформировать и отправить сообщение;
- ответить на сообщение.



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа Outlook:** 

1. **Имя аккаунта\*** *[String]* - имя аккаунта, от которого будет отправлено сообщение. Обязательный параметр.
2. **Переменная** *[[LTools.Office.Model.OMailMessage](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailmessage)]* - название переменной, хранящей данные отправляемого сообщения. Использование переменной позволяет сразу отправить готовое сообщение, пропустив остальные свойства элемента. Для этого переменную заранее нужно создать в коде.
3. **Тема** *[String]* - тема сообщения. 
4. **Тело письма** *[String]* - тело отправляемого сообщения. Если одновременно указано свойство **Переменная**, то приоритет будет у свойства **Тело письма**.
5. **Вложения** *[List\<String>]* - путь к файлу вложения письма.
6. **Кому** *[String]* - адресат сообщения.
7. **Копия** *[String]* - адресат копии. Если их несколько, используйте разделительный символ ";".
8. **Скрытая копия** *[String]* - адресат скрытой копии. Если их несколько, используйте разделительный символ ";".
9. **Формат** *[[LTools.Office.Model.OMailMessage.MailFormats](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/mailformats)]* - формат сообщения.
10. **От имени (адрес)** *[String]* - заполняется в случае необходимости изменить отправителя сообщения. В значении необходимо указать почту. Пример: `"ivanov_ivan@mail.ru"`. Если не заполнено, то по умолчанию письмо будет отправлено от имени владельца аккаунта.
11. **От имени (отображаемое имя)** *[String]* - отображаемое имя отправителя письма. Используется по желанию и только при условии, если заполнено свойство **От имени (адрес)**. Для указания отображаемого имени необходимо иметь соответствующие права, иначе возникнет ошибка.

**Группа Re:**

1. **Ответить** *[LTools.Office.Model.OMailMessage]* - название переменной с данными письма, на которое вы хотите ответить. Если одновременно заполнено свойство **Переменная**, то приоритет будет у свойства **Ответить**.                                   
2. **Ответить всем** *[Boolean]* - если флаг установлен, то ответ отправится всем адресатам.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
LTools.Office.Model.OMailMessage msg = new LTools.Office.Model.OMailMessage() { Subject = "subject", Body = "body" };
app.SendMessage(msg, "My");
app.SendMessage("body", "sendTo", "subject", "My", new List<string>() { "file1" }, LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
msg = LTools.Office.Model.OMailMessage() 
msg.Subject = "subject"
msg.Body = "body"
app.SendMessage(msg, "My")
att = List[String]()
att.Add("file1")
app.SendMessage("body", "sendTo", "subject", "My", att, LTools.Office.Model.OMailMessage.MailFormats.HTML)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
var msg = host.newObj(_lib.LTools.Office.Model.OMailMessage); 
msg.Subject = "subject";
msg.Body = "body";
var att = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
att.Add("file1");
app.SendMessage(msg, "My");
app.SendMessage("body", "sendTo", "subject", "My", att, _lib.LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}
{% endtabs %}



