# Отправить сообщение

![](<../../../.gitbook/assets/image (73).png>)

Выполняет отправку электронной почты через Outlook. Элемент корректно работает только внутри контейнера [**Приложение Outlook**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook).

Общие свойства элемента описаны [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements). Утилитарные приведены в таблице ниже.

| Свойство       | Тип                                                                      | Описание                                              
| -------------- | ------------------------------------------------------------------------ | ---------------------------------------------------- 
| Имя аккаунта   | String                                                                   | Имя аккаунта, от которого будет отправлено сообщение. Обязательно для заполнения 
| Переменная     | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md)| Данные отправляемого сообщения                      
| Тема           | String                                                                   | Тема сообщения                                       
| Тело письма    | String                                                                   | Тело отправляемого сообщения                        
| Вложения       | List\<String>                                                            | Путь к файлу вложения письма                         
| Кому           | String                                                                   | Адресат сообщения                                    
| Копия          | String                                                          | Адресат копии. Если их несколько, указывайте через символ ";"
| Скрытая копия  | String                                                          | Адресат копии. Если их несколько, указывайте через символ ";"
| Формат         | [LTools.Office.Model.OMailMessage.MailFormats](../els\_mail/datatypes/mailformats.md) | Формат сообщения                        
| От имени       | String   | Заполняется в случае необходимости изменить отправителя сообщения. В значении необходимо указать почту. Пример: "iv_ivan@mail.ru". Если не заполнено, то по умолчанию письмо будет отправлено от владельца аккаунта | Нет
| **Группа Re:** |  |                  |
| Ответить       | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md) | Ответить на письмо                                    
| Ответить всем  | Boolean                                                                    | Если флаг установлен, ответ отправится всем адресатам 


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



