# OMailMessage

LTools.Office.Model.OMailMessage - модель письма. Используется в элементах, работающих с почтами Outlook, Exchange, Lotus Notes.

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению по его ID. Получить ID можно при считывании писем соответствующими элементами Студии. Например, в результате [Чтения почты](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) получаем список писем, у каждого из которых есть свой ID |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма. Пример значения: `HTML`. Также может быть PLAIN (простой текст) или Rich Text (расширенный текст) |
| MessageType | LTools.Office.Model.OMailMessage.MailTypes                      | Только для Outlook. Тип письма. Пример значения: `Message` или `Report` (отчет о доставке) |
| From        | String                                                          | От кого. Содержит адрес электронной почты отправителя. Пример: `user@mail.ru` |
| To          | List\<String>                                                   | Кому - список адресов получателей сообщения |
| Сс          | List\<String>                                                   | Список адресов получателей копии сообщения  |
| Всс         | List\<String>                                                   | Список получателей скрытой копии сообщения  |
| CreateDate  | [System.DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=netframework-4.8) | Дата и время создания письма. Пример значения: `13.07.2023 18:21:25`  |
| ReceiveDate | System.DateTime                                                 | Дата и время получения письма  |
| Subject     | String                                                          | Тема письма                    |
| ConversationTopic | String                                                    | Только для Outlook. Тема для потока беседы. Беседа содержит все связанные сообщения в одной беседе с одинаковой строкой темы. Темой беседы обычно является тема первого сообщения электронной почты в потоке. Подробнее о беседах в Outlook см. [здесь](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D1%89%D0%B8%D0%B5-%D1%81%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BE-%D0%B1%D0%B5%D1%81%D0%B5%D0%B4%D0%B0%D1%85-0eeec76c-f59b-4834-98e6-05cfdfa9fb07). При чтении письма в Outlook могут быть заполнены как Subject, так и ConversationTopic. Пример значений для отправленного письма: Subject - `"Re: Отпуск"`,  ConversationTopic - `"Отпуск"` |
| Body        | String                                                          | Текст тела письма. **В Exchange** тело будет представлено **только в HTML**, в Outlook - может быть и в виде простого текста (PLAIN). Простой текст не поддерживает картинки, гиперссылки (вместо них будут обычные ссылки) и другие подобные элементы. Пример значения для PLAIN: `"Текст\n"`. Если считывается беседа, то тело будет включать все письма беседы |
| HTMLBody    | String                                                           | Текст тела письма в формате HTML  |
| MessageProperties | LTools.Office.Model.OMailMessage.OMailProperties  | Только для Outlook. Свойства письма. Отображаются, если в элементе [Чтение почты](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) установлен флаг **Читать свойства**. С помощью свойств письма можно узнать, например, отображаемое имя отправителя/получателя   |
| Element     | [Microsoft.Exchange.WebServices.Data.EmailMessage](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.exchange.webservices.data.emailmessage?view=exchange-ews-api) | Представляет сообщение электронной почты. Тип данных зависит от используемой почты: для Exchange - это EmailMessage, для Outlook - это MailItem, для Lotus - это Domino.NotesDocument. Чтобы получить доступ к свойствам класса, требуется сначала вручную привести его к нужному типу. Подробнее см. в подразделе ниже  |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения письма   |

:small_blue_diamond: **Примечание**. Все свойства, начинающиеся со слова **Send**, а также свойство **ReplyAll** содержат только техническую информацию и не предназначены для пользователей. Это такие свойства, как: SendTo, SendСс, SendВсс, SendOnBehalf, ReplyAll. 


## Детализация свойств модели
1\. **CreateDate** имеет свойства, представленные на рисунке ниже:

![](<../../../../.gitbook/assets/omail-createdate.png>)

Пример получения дня месяца, когда было создано сообщение: `var_list_mails[0].CreateDate.Day`, где:
* var_list_mails - это условное название переменной;
* [0] - индекс письма, свойство которого хотим получить. 

Если используется вывод результата через элемент [**Запись в журнал**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_dialogs/el_dialogs_addlog), не забудьте привести значение к строке. Пример результата: `13`.

2\. **MessageProperties** (только Outlook) обладает свойствами, представленными на рисунке ниже. Пример получения отображаемого имени отправителя: `var_list_mails[0].MessageProperties.PR_SENDER_NAME`. 

![](<../../../../.gitbook/assets/omail-message-properties2.png>)

| Свойство        | Тип        | Описание                     |
| --------------- | ---------- | ---------------------------- |
| PR_DISPLAY_TO   | String     | Отображаемое имя получателя (-ей) письма. Пример: `"Константин Бальмонт, Зинаида Гиппиус"` |
| PR_DISPLAY_BCC  | String     | Отображаемое имя получателя скрытой копии, если таковой имеется |
| PR_DISPLAY_CC   | String     | Отображаемое имя получателя копии         |
| PR_RECEIVED_BY_EMAIL_ADDRESS | String  | Адрес электронной почты получателя сообщения (?? у меня здесь был адрес отправителя, а не получателя - это видно на скрине). Подробнее см. [здесь](https://learn.microsoft.com/ru-RU/office/client-developer/outlook/mapi/pidtagreceivedbyemailaddress-canonical-property). Пример: `/O=CS24 EXCHANGE/OU=EXCHANGE ADMINISTRATIVE GROUP (FYDIBOHF23SPDLT)/CN=RECIPIENTS/CN=361786F4F0444280A5B6FAF5AE5A79D3-USER` -  это стандартный вид для этого поля? как его расшифровать? Почему совпадает с PR_SENDER_EMAIL_ADDRESS? |
| PR_RECEIVED_BY_NAME | String | Отображаемое имя истинного получателя сообщения (??? у меня здесь высветилось имя отправителя). Задается поставщиком входящего транспорта. Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagreceivedbyname-canonical-property) |
| PR_REPLY_RECIPIENT_NAMES | String | Список отображаемых имен пользователей, которые должны получить ответ. Если это свойство отсутствует, ответ отправляется только пользователю, идентифицируему свойством PR_SENDER_NAME. Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagreplyrecipientnames-canonical-property) |
| PR_SENDER_NAME          | String  | Отображаемое имя отправителя сообщения. Пример: `"Андрей Белый"`. Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagsendername-canonical-property) |
| PR_SENDER_EMAIL_ADDRESS  | String | Адрес почты отправителя. Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagsenderemailaddress-canonical-property). Пример значения: `/O=CS24 EXCHANGE/OU=EXCHANGE ADMINISTRATIVE GROUP (FYDIBOHF23SPDLT)/CN=RECIPIENTS/CN=361786F4F0444280A5B6FAF5AE5A79D3-USER` - это стандартный вид для этого поля?  |
| PR_SENT_REPRESENTING_EMAIL_ADDRESS | String   | Адрес электронной почты отправителя сообщения (в чем разница с PR_SENDER_EMAIL_ADDRESS?). Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagsentrepresentingemailaddress-canonical-property) |
| PR_SENT_REPRESENTING_NAME          | String   | Отображаемое имя отправителя сообщения (в чем разница с PR_SENDER_NAME?). Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagsentrepresentingname-canonical-property) |
| PR_TRANSPORT_MESSAGE_HEADERS       | String   | Сведения о конверте сообщений, относящихся к транспорту. Поставщик транспорта может создавать сведения о заголовке сообщения для входящих сообщений. Подробнее см. [здесь](https://learn.microsoft.com/ru-ru/office/client-developer/outlook/mapi/pidtagtransportmessageheaders-canonical-property)  |

3\. **Element** - почтовое сообщение. Тип данных зависит от используемой почты: 
* для Exchange - это [EmailMessage](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.exchange.webservices.data.emailmessage?view=exchange-ews-api);
* для Outlook - это [Microsoft.Office.Interop.Outlook.MailItem](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.office.interop.outlook.mailitem?view=outlook-pia);
* для Lotus - это [Domino.NotesDocument]().

Список свойств будет соответствовать классу сообщения. 

:bangbang: **Важно.** Для того, чтобы получить значение какого-либо свойства Element, требуется вручную привести его к нужному классу. 

Например, чтобы получить имя отправителя для сообщения Exchange, приведите его сначала к EmailMessage: `(var_list_mails[0].Element as Microsoft.Exchange.WebServices.Data.EmailMessage).Sender`. 









