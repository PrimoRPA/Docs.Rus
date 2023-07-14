# OMailMessage

LTools.Office.Model.OMailMessage - модель письма.

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению. Получить ID можно при считывании писем соответствующими элементами Студии. Например, в результате [**Чтения почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) получаем список писем, у каждого из которых есть свой ID |
| From        | String                                                          | От кого. Содержит адрес электронной почты отправителя. Пример: `user@mail.ru`|
| To          | List\<String>                                                   | Кому (для входящих). Список адресов получателей сообщения |
| SendTo      | String                                                          | Кому (для отправленных). Список адресов получателей сообщения (список или только один адрес? тип данных не указан. Все свойства со словом Send - это для папки "Отправленные"?) |
| Сс          | List\<String>                                                   | Список получателей копии сообщения                |
| Всс         | List\<String>                                                   | Список получателей скрытой копии сообщения        |
| CreateDate  | [System.DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=netframework-4.8) | Дата и время создания письма. Пример значения: `13.07.2023 18:21:25`  |
| ReceiveDate | System.DateTime                                                 | Дата и время получения письма  |
| Subject     | String                                                          | Тема письма      |
| ConversationTopic |                                                           | Тема беседы               |
| Body        | String                                                          | Текст тела письма     |
| Element     | [Microsoft.Exchange.WebServices.Data.EmailMessage](https://learn.microsoft.com/ru-ru/dotnet/api/microsoft.exchange.webservices.data.emailmessage?view=exchange-ews-api) | Класс, представляющий сообщение электронной почты. Свойства класса доступны для просмотра только при использовании элементов MS Exchange    |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма. Пример значения: `HTML` |
| MessageType |  | Тип письма. Пример значения: `Message` (Вопрос Мише: какие бывают?) |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения             |


## Детализация
1\. Свойство **CreateDate** имеет атрибуты, представленные на рисунке ниже:

![](<../../../../.gitbook/assets/omail-createdate.png>)

Пример вызова в редакторе одного из представленных полей: `var_list_mails[0].CreateDate.Day`

2\. Класс **Element** обладает свойствами, представленными на рисунке ниже: 








