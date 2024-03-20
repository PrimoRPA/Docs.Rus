---
description: Send message
---

# Отправить сообщение

Элемент предназначен для отправки писем через почту MS Exchange. С его помощью возможно:
* сформировать и отправить сообщение;
* ответить на какое-либо сообщение.

Данный элемент размещается внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_connect). Перед отправкой сообщения убедитесь, что в контейнере правильно указаны все необходимые свойства: email, логин, пароль и др. 

![](<../../../../.gitbook/assets1/exchange-send-message.png>)




## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа Exchange:** 

1. **Кому\*** *[String]* — электронный адрес адресата. Обязательный параметр. В случае, если указан только адресат, а все остальные параметры не заполнены, то будет отправлено пустое письмо. 
1. **Кому (в копии)** *[String]* — электронный адрес адресата копии. Если их несколько, используйте разделительный символ ";".
1. **Скрытая копия** *[String]* — электронный адрес адресата скрытой копии. Если их несколько, используйте разделительный символ ";".     
1. **Переменная** *[[LTools.Office.Model.OMailMessage](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailmessage)]* — название переменной с моделью письма. В настоящее время не рекомендуется к использованию.
1. **Тема** *[String]* — тема сообщения.          
1. **Тело письма** *[String]* — тело отправляемого сообщения. Пример: `"Message text"`.
1. **Формат** *[[LTools.Office.Model.OMailMessage.MailFormats](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/mailformats)]* — формат сообщения. По умолчанию `PLAIN` - простой текст, не поддерживающий картинки, гиперссылки и другие подобные элементы. Чтобы изменить формат, нажмите на выпадающий список значений. Доступны варианты: `RICHTEXT`, `HTML`.
1. **Вложения** *[System.Collections.Generic.List\<String>]* — список путей к вложениям письма. Указать пути можно несколькими способами:
   * Использовать редактор коллекций (1). В поле редактора пропишите путь до файла вложения либо переменную, содержащую путь (2). Новая строка добавляется по нажатию `Enter`.

     ![](<../../../../.gitbook/assets1/collection-editor-exchange.png>)

   * Заранее подготовить список путей до вложений. Его можно сформировать вручную или использовать элемент [Поиск файлов](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_files/el_files_search), чтобы сохранить пути найденных вложений в переменную.
1. **Копировать в папку** *[Boolean]* — определяет, нужно ли сохранять копию письма в папке «Отправленные». По умолчанию чекбокс выключен — копия не сохраняется.
1. **Папка копирования** *[String]* — позволяет переопределить папку для хранения копии письма. Работает только при установке чекбокса **Копировать в папку**. 
1. **От имени** *[String]* — изменяет адрес отправителя письма. В значении укажите электронный адрес и убедитесь, что у вас есть право на отправку писем с этого ящика — разрешение «Отправить как» (Send as). Получатель в данном случае не увидит, что письмо ему отправил другой пользователь. Если значение не задано, то отправителем будет владелец учетной записи, под которой вы подключились к серверу Exchange. 
1. **Общий ящик** *[String]* — позволяет сохранить копию отправленного письма в общем почтовом ящике. В значении нужно указать адрес общего ящика, участником которого вы являетесь. Одновременно с этим должны быть заполнены свойства:
   * **Копировать в папку** — иначе копия не сохранится.
   * **От имени** — если нужно не только сохранить копию в общем ящике, но и произвести саму отправку из общего ящика. 
   * **Папка копирования** — если письмо нужно сохранить в папке, отличной от «Отправленные».
   

**Группа Re:** 

1. **Ответить** *[LTools.Office.Model.OMailMessage]* — название переменной с данными письма, на которое вы хотите ответить. Такую переменную можно получить, если предварительно использовать в сценарии элемент [**Чтение почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_read).
2. **Ответить всем** *[Boolean]* — если флаг установлен, ответ будет выслан всем адресатам.       



## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
LTools.Office.Model.OMailMessage msg = new LTools.Office.Model.OMailMessage() { Subject = "subject", Body = "body" };
app.SendMessage(msg);
app.SendMessage("body", "sendTo", "subject", new List<string>() { "file1" }, LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = LTools.Office.Model.OMailMessage() 
msg.Subject = "subject"
msg.Body = "body"
app.SendMessage(msg)
att = List[String]()
att.Add("file1")
app.SendMessage("body", "sendTo", "subject", att, LTools.Office.Model.OMailMessage.MailFormats.HTML)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = host.newObj(_lib.LTools.Office.Model.OMailMessage); 
msg.Subject = "subject";
msg.Body = "body";
var att = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
att.Add("file1");
app.SendMessage(msg);
app.SendMessage("body", "sendTo", "subject", att, _lib.LTools.Office.Model.OMailMessage.MailFormats.HTML);
```
{% endtab %}
{% endtabs %}

