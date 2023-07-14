# OMailMessage

LTools.Office.Model.OMailMessage - модель письма.

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению. Получить ID можно при считывании писем соответствующими элементами Студии. Например, в результате [**Чтения почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) получаем список писем, у каждого из которых есть свой ID |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма. Пример значения: `HTML` |
| MessageType |  | Тип письма. Пример значения: `Message` (Вопрос Мише: какие бывают?) |
| From        | String                                                          | От кого. Содержит адрес электронной почты отправителя. Пример: `user@mail.ru` |
| To          | List\<String>                                                   | Для входящих. Кому - список адресов получателей сообщения |
| Сс          | List\<String>                                                   | Для входящих. Список адресов получателей копии сообщения  |
| Всс         | List\<String>                                                   | Для входящих. Список получателей скрытой копии сообщения |
| SendTo      | String                                                          | Для отправленных. Кому - список адресов получателей сообщения (список или только один адрес? тип данных не указан. Все свойства со словом Send - это для папки "Отправленные"?) |
| SendСс      | List\<String>                                                   | Для отправленных. Список получателей копии сообщения |
| SendВсс     | List\<String>                                                   | Для отправленных. Список получателей скрытой копии сообщения  |
| SendOnBehalf | Какой тип данных? String?                                      | Для отправленных. От какого имени было отправлено письмо. Содержит значение в случае, если отправка осуществлялась [от имени другого лица](https://support.microsoft.com/en-us/office/send-email-on-behalf-of-someone-else-dbaf0b80-df07-4a4d-90c7-8dbd63d5ddac) |
| ReplyAll    | Boolean                                                         | ? для отпр или для вход?  Пример значения: `False`  |
| CreateDate  | [System.DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=netframework-4.8) | Дата и время создания письма. Пример значения: `13.07.2023 18:21:25`  |
| ReceiveDate | System.DateTime                                                 | Дата и время получения письма  |
| Subject     | String                                                          | Тема письма      |
| ConversationTopic |                                                           | Тема беседы (что за беседа?)              |
| Body        | String                                                          | Текст тела письма     |
| HTMLBody    | Тип данных?                                                     | Текст тела письма в формате HTML (в чем разница с body? он всегда в html - баг или фича) |
| MessageProperties | Какой тип данных? | Свойства письма.  |
| Element     | [Microsoft.Exchange.WebServices.Data.EmailMessage](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.exchange.webservices.data.emailmessage?view=exchange-ews-api) | Класс, представляющий сообщение электронной почты. Свойства класса доступны для просмотра только при использовании элементов MS Exchange    |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения             |


## Детализация
1\. Свойство **CreateDate** имеет атрибуты, представленные на рисунке ниже:

![](<../../../../.gitbook/assets/omail-createdate.png>)

Пример вызова в редакторе одного из представленных полей: `var_list_mails[0].CreateDate.Day`

2\. Класс **Element** обладает свойствами, представленными на рисунке ниже: 

![](<../../../../.gitbook/assets/>)


3\. **MessageProperties** обладает свойствами, представленными на рисунке ниже: 

![](<../../../../.gitbook/assets/>)

4\. Пример тела письма, полученного в свойстве **Body**:

![](<../../../../.gitbook/assets/>)







