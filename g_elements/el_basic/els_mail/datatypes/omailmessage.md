# OMailMessage

LTools.Office.Model.OMailMessage - модель письма.

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению. Получить ID можно при считывании писем соответствующими элементами Студии. Например, в результате [**Чтения почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail) получаем список писем, у каждого из которых есть свой ID |
| From        | String                                                          | От кого. Пример: `user@domen.ru`  |
| To          | List\<String>                                                   | Кому (для входящих)  |
| SendTo      | String                                                          | Кому (отправить)     |
| ReceiveDate | [DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=netframework-4.8) | Дата и время получения письма  |
| Subject     | String                                                          | Тема письма      |
| Body        | String                                                          | Текст тела письма     |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма     |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения             |





