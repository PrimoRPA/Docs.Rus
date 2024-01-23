---
description: Send message
---

# Отправить сообщение

Предназначен для отправки писем через почту MS Exchange. Размещается внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_connect). Перед использованием элемента **Отправить сообщение** убедитесь, что в контейнере правильно указаны все необходимые свойства: email, логин, пароль и др. 

![](<../../../../.gitbook/assets1/exchange-send-message.png>)

Применение элемента **Отправить сообщение** позволяет:
* сформировать и отправить сообщение;
* ответить на какое-либо сообщение.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа Exchange:** 

1. **Кому\*** *[String]* - электронный адрес адресата. Обязательный параметр. В случае, если указан только адресат, а все остальные параметры не заполнены, то будет отправлено пустое письмо. 
1. **Кому (в копии)** *[String]* - электронный адрес адресата копии. Если их несколько, используйте разделительный символ ";".
1. **Скрытая копия** *[String]* - электронный адрес адресата скрытой копии. Если их несколько, используйте разделительный символ ";".     
1. **Переменная** *[[LTools.Office.Model.OMailMessage](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailmessage)]* - название переменной с моделью письма. Использование переменной позволяет сразу отправить готовое сообщение, пропустив необязательные свойства элемента. Для этого ее нужно сначала создать в коде, после чего указать в этом свойстве. 
1. **Тема** *[String]* - тема сообщения, если имеется.          
1. **Тело письма** *[String]* - тело отправляемого сообщения. Пример: `"Message text"`.
1. **Вложения** *[System.Collections.Generic.List\<String>]* - пути к файлам вложений письма. Указать пути можно несколькими способами:
   * Использовать редактор коллекций (1). В поле редактора укажите путь до файла (2) либо переменную, содержащую этот путь. По нажатию клавиши `Enter` добавляется новая строка, куда можно вписать путь/переменную до другого файла.

     ![](<../../../../.gitbook/assets1/collection-editor-exchange.png>)

   * Заранее подготовить список (List\<String>) и затем передать его в свойство **Вложения**. Список путей можно сформировать вручную или, к примеру, использовать элемент **Файловая система > [Поиск файлов](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_files/el_files_search)**, чтобы найти файлы в заданной папке и сохранить пути в переменную.
1. **Формат** *[[LTools.Office.Model.OMailMessage.MailFormats](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/mailformats)]* - формат сообщения. По умолчанию `PLAIN` - простой текст, не поддерживающий картинки, гиперссылки и другие подобные элементы. Чтобы изменить формат, нажмите на выпадающий список значений. Доступны варианты: `RICHTEXT`, `HTML`.
1. **Копировать в папку** *[Boolean]* - определяет, нужно ли сохранять копию отправленного письма. При установке чекбокса копия сохранится в папку «Отправленные» - если папку нужно изменить, заполните свойство **Папка копирования**. По умолчанию чекбокс выключен - копия не сохраняется.
1. **Папка копирования** *[String]* - название почтовой папки для сохранения копии отправленного письма. Пример: `"mail folder"`. Работает только при установке чекбокса **Копировать в папку**. 
1. **От имени (адрес)** *[String]* - заполняется при необходимости изменить отправителя, указанного в контейнере MS Exchange. В значении укажите почтовый адрес, с которого следует произвести отправку. При этом адрес должен входить в список разрешенных на почтовом сервере (подробнее см. [здесь](https://docs.microsoft.com/ru-ru/microsoft-365/admin/email/add-another-email-alias-for-a-user?view=o365-worldwide) и [здесь](https://docs.microsoft.com/ru-ru/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user?view=o365-worldwide)). Если значение не задано, то отправителем по умолчанию будет являться владелец учетной записи, под которой осуществляется подключение к серверу MS Exchange.
1. **От имени (отображаемое имя)** *[String]* - отображаемое имя отправителя письма. Указывается в дополнение к свойству ***От имени (адрес)** - если адрес не задан, то отображаемое имя тоже проигнорируется. Для указания имени необходимо иметь соответствующие права, иначе возникнет ошибка.
1. **Общий ящик** *[String]* - позволяет сохранить копию отправленного письма в [общем почтовом ящике](https://learn.microsoft.com/ru-ru/exchange/collaboration/shared-mailboxes/shared-mailboxes?view=exchserver-2019&viewFallbackFrom=exchserver-2013). В значении нужно указать адрес общего ящика, участником которого вы являетесь. Пример: `"info@contoso.com"`. Одновременно с этим должны быть заполнены свойства:
   * **Копировать в папку** - иначе копия не сохранится;
   * **Папка копирования** - если письмо нужно сохранить в папке, отличной от "Отправленные";
   * **От имени (адрес)** - если нужно не только сохранить копию в общем ящике, но и произвести саму отправку из общего ящика. 

**Группа Re:** 

1. **Ответить** *[LTools.Office.Model.OMailMessage]* - название переменной с данными письма, на которое вы хотите ответить. Такую переменную можно получить, если предварительно использовать в сценарии элемент [**Чтение почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/els_exchange/el_read).
2. **Ответить всем** *[Boolean]* - если флаг установлен, ответ будет выслан всем адресатам.       



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

