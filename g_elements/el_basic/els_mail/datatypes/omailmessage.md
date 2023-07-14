# OMailMessage

LTools.Office.Model.OMailMessage - модель письма.

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению. Получить ID можно при считывании писем соответствующими элементами Студии. Например, в результате [**Чтения почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) получаем список писем, у каждого из которых есть свой ID |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма. Пример значения: `HTML`. Также может быть PLAIN (простой текст) или Rich Text (расширенный текст) |
| MessageType | LTools.Office.Model.OMailMessage.MailTypes                      | Тип письма. Пример значения: `Message` |
| From        | String                                                          | От кого. Содержит адрес электронной почты отправителя. Пример: `user@mail.ru` |
| To          | List\<String>                                                   | Кому. Список адресов получателей сообщения |
| Сс          | List\<String>                                                   | Список адресов получателей копии сообщения  |
| Всс         | List\<String>                                                   | Список получателей скрытой копии сообщения |
| ReplyAll    | Boolean                                                         | Ответить всем. Определяет, было ли отправлено письмо исходному отправителю и всем остальным получателям из строки "Кому". Пример значения: `False` - ответ всем не использовался |
| CreateDate  | [System.DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=netframework-4.8) | Дата и время создания письма. Пример значения: `13.07.2023 18:21:25`  |
| ReceiveDate | System.DateTime                                                 | Дата и время получения письма  |
| Subject     | String                                                          | Тема письма                    |
| ConversationTopic | String                                                    | Только для Outlook. Тема для потока беседы. Беседа содержит все связанные сообщения в одной беседе с одинаковой строкой темы. Темой беседы обычно является тема первого сообщения электронной почты в потоке. Подробнее о беседах в Outlook см. [здесь](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D1%89%D0%B8%D0%B5-%D1%81%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BE-%D0%B1%D0%B5%D1%81%D0%B5%D0%B4%D0%B0%D1%85-0eeec76c-f59b-4834-98e6-05cfdfa9fb07). При чтении письма в Outlook могут быть заполнены как Subject, так и ConversationTopic. Пример значений для отправленного письма: Subject - `"Re: Скоро отпуск"`,  ConversationTopic - `"Скоро отпуск"` |
| Body        | String                                                          | Текст тела письма. **В Exchange** тело будет представлено здесь **только в HTML**, в Outlook - может быть в виде простого текста (PLAIN). Простой текст не поддерживает картинки, гиперссылки (вместо них будут ссылки с синим подчеркиванием) и другие подобные элементы. Пример значения для PLAIN: `"Текст\n"`. Если это беседа, то тело будет включать все письма беседы (и в Exchange, и в Outlook) |
| HTMLBody    | String                                                          | Только для Outlook, в Exchange - пустое. Текст тела письма в формате HTML  |
| MessageProperties | LTools.Office.Model.OMailMessage.OMailProperties  | Только для Outlook. Свойства письма. Отображаются только, если в [**Чтении почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) установлен флаг "Читать свойства"  |
| Element     | [Microsoft.Exchange.WebServices.Data.EmailMessage](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.exchange.webservices.data.emailmessage?view=exchange-ews-api) | Только для MS Exchange. Класс, представляющий сообщение электронной почты  |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения письма            |

:small_blue_diamond: **Примечание**:

Все свойства, начинающиеся со слова **Send**, в настоящее время не несут информации и имеют пустое значение. Это такие свойства, как: SendTo, SendСс, SendВсс, SendOnBehalf.


## Детализация свойств модели
1\. **CreateDate** имеет свойства, представленные на рисунке ниже:

![](<../../../../.gitbook/assets/omail-createdate.png>)

Пример вызова в редакторе одного из полей: `var_list_mails[0].CreateDate.Day`.

2\. **MessageProperties** обладает свойствами, представленными на рисунке ниже: 

![](<../../../../.gitbook/assets/omail-message-properties.png>)

2\. Класс **Element** обладает свойствами, представленными на рисунке ниже: 

![](<../../../../.gitbook/assets/>)










