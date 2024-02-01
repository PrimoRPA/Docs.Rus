---
description: Send message
---

# Отправить сообщение

Элемент выполняет отправку электронного письма через Outlook. Размещается внутри контейнера [**Приложение Outlook**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook/el_outlook_app).

![](<../../../.gitbook/assets1/outlook-send-message.png>)

Применение элемента позволяет достичь следующих целей:
- сформировать и отправить сообщение;
- ответить на сообщение.


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа Outlook:** 

1. **Имя аккаунта** *[String]* - имя учетной записи в профиле Outlook, c адреса которой необходимо отправить письмо. Если в профиле только одна учетная запись, то свойство можно не заполнять. Имя аккаунта можно узнать в меню **Файл > Настройка учетных записей** в Outlook. Пример:

    ![](<../../../.gitbook/assets1/account-name.png>)
   
    Если указанное имя не будет найдено среди аккаунтов запущенного профиля Outlook, то для отправки сообщения будет использован аккаунт по умолчанию. 
1. **Переменная** *[[LTools.Office.Model.OMailMessage](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/omailmessage)]* - название переменной, хранящей данные письма. Использование переменной позволяет сразу отправить сообщение, которое вы сформировали в коде, и пропустить заполнение необязательных свойств элемента. Если одновременно указать и переменную, и свойства - что не рекомендуется - то приоритет будет у значений из свойств.
1. **Тема** *[String]* - тема сообщения. 
1. **Тело письма** *[String]* - тело отправляемого сообщения. 
1. **Вложения** *[List\<String>]* - путь к файлу вложения письма. Используйте редактор коллекций, чтобы указать путь каждого вложения - список сформируется автоматически.

    ![](<../../../.gitbook/assets1/collection-editor-outlook.png>)
    
1. **Кому** *[String]* - адресат сообщения.
1. **Копия** *[String]* - адресат копии. Если их несколько, используйте разделительный символ ";".
1. **Скрытая копия** *[String]* - адресат скрытой копии. Если их несколько, используйте разделительный символ ";".
1. **Формат** *[[LTools.Office.Model.OMailMessage.MailFormats](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_mail/datatypes/mailformats)]* - формат сообщения. По умолчанию `PLAIN` - простой текст, не поддерживающий картинки, гиперссылки и другие подобные элементы. Чтобы изменить формат, нажмите на выпадающий список значений. Доступны варианты: `RICHTEXT`(RTF), `HTML`.
1. **От имени (адрес)** *[String]* - позволяет изменить адрес отправителя. В значении можно указать [общий ящик](https://support.microsoft.com/ru-ru/office/%D0%BE%D1%82%D0%BA%D1%80%D1%8B%D1%82%D0%B8%D0%B5-%D0%B8-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D0%BE%D0%B2%D0%B0%D0%BD%D0%B8%D0%B5-%D0%BE%D0%B1%D1%89%D0%B5%D0%B3%D0%BE-%D0%BF%D0%BE%D1%87%D1%82%D0%BE%D0%B2%D0%BE%D0%B3%D0%BE-%D1%8F%D1%89%D0%B8%D0%BA%D0%B0-%D0%B2-outlook-d94a8e9e-21f1-4240-808b-de9c9c088afd), участником которого вы являетесь. Если вы указали общий ящик, убедитесь, что обладаете правами на отправку писем - разрешением [«Отправить как»](https://learn.microsoft.com/ru-ru/exchange/collaboration/shared-mailboxes/shared-mailboxes?view=exchserver-2019#what-are-shared-mailboxes) (Send as). Если свойство не заполнено, то по умолчанию письмо будет отправлено с основного адреса, привязанного к учетной записи.
1. **От имени (отображаемое имя)** *[String]* - отображаемое имя отправителя письма. Используется в дополнение к свойству **От имени (адрес)** - если оно пустое, отображаемое имя тоже проигнорируется. Для отправки письма [от имени другого пользователя](https://learn.microsoft.com/ru-ru/microsoft-365/admin/add-users/give-mailbox-permissions-to-another-user?view=o365-worldwide#send-email-on-behalf-of-another-user) или от имени общего ящика у вас должно быть разрешение "Отправить от имени", выданное администратором, иначе возникнет ошибка.


**Группа Re:**

1. **Ответить** *[LTools.Office.Model.OMailMessage]* - название переменной с данными письма, на которое вы хотите ответить. Такую переменную можно получить, если предварительно использовать в сценарии элемент [**Чтение почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_outlook/el_outlook_readmail).

   :small_orange_diamond: *Если одновременно заполнить свойства **Переменная** и **Ответить**, то приоритет будет у **Ответить**.*                         

2. **Ответить всем** *[Boolean]* - если флаг установлен, то ответ отправится всем адресатам.


### Решение проблем 

1. Выполнение/отладка элемента, в котором заполнены свойства **От имени (адрес)** и **От имени (отображаемое имя)**, может завершиться ошибкой:
```
"Error: Отправить сообщение/cf63d3fd-495d-4cc7-b82b-acaea13d362c/1.1/LTools.Office.Elements.Outlook.WFSendMessage = Не удалось выполнить операцию. Интерфейс передачи сообщений возвратил неизвестную ошибку. Если это повторится, перезагрузите Outlook. Невозможно определить получателя".
```

Это означает, что у пользователя недостаточно прав на использование функциональности и необходимо связаться с администратором почты.


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



