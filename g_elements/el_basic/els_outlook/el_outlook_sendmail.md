# Отправить сообщение

*Send message*

![](<../../../.gitbook/assets/image (73).png>)

Элемент выполняет отправку электронного письма через Outlook. Размещается внутри контейнера [**Приложение Outlook**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook).

Применение элемента позволяет достичь следующих целей:
- сформировать и отправить сообщение;
- ответить на сообщение.



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип                                                                      | Описание                                              
| -------------- | ------------------------------------------------------------------------ | ---------------------------------------------------- 
| **Группа Outlook:** |  |    |
| Имя аккаунта   | String                                                                   | Имя аккаунта, от которого будет отправлено сообщение. Обязательно для заполнения 
| Переменная     | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)| Данные отправляемого сообщения. Эту переменную можно заранее создать в коде и, таким образом, сразу отправить готовое сообщение                     
| Тема           | String                                                                   | Тема сообщения                                       
| Тело письма    | String                                                                   | Тело отправляемого сообщения. Если одновременно заполнено это свойство и свойство **Переменная**, то приоритет будет у свойства **Тело письма**                            
| Вложения       | List\<String>                                                            | Путь к файлу вложения письма                         
| Кому           | String                                                                   | Адресат сообщения                                    
| Копия          | String                                                                   | Адресат копии. Если их несколько, указывайте через символ ";"
| Скрытая копия  | String                                                                   | Адресат копии. Если их несколько, указывайте через символ ";"
| Формат         | [LTools.Office.Model.OMailMessage.MailFormats](../els\_mail/datatypes/mailformats.md) | Формат сообщения                        
| От имени (адрес) | String   | Заполняется в случае необходимости изменить отправителя сообщения. В значении необходимо указать почту. Пример: `"iv_ivan@mail.ru"`. Если не заполнено, то по умолчанию письмо будет отправлено от владельца аккаунта | Нет
| **Группа Re:** |  |    |
| Ответить       | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md) | Ответить на письмо. Если одновременно заполнено это свойство и свойство **Переменная**, то приоритет будет у свойства **Ответить**                                    
| Ответить всем  | Boolean                                                                    | Если флаг установлен, то ответ отправится всем адресатам 

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



