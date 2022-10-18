# OMailMessage

LTools.Office.Model.OMailMessage

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению. Получить ID можно при считывании писем с помощью соответствующих элементов Студии. Например, при использовании [**Чтения почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail), в результате которого мы получаем список писем, у каждого из которых есть свой ID |
| Body        | String                                                          | Текст тела письма    |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма        |
| Subject     | String                                                          | Тема письма          |
| From        | String                                                          | От кого              |
| SendTo      | String                                                          | Кому (отправить)     |
| To          | List\<String>                                                   | Кому (для входящих)  |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения             |

