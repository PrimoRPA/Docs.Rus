# OMailMessage

LTools.Office.Model.OMailMessage

| Свойство    | Тип                                                             | Описание             |
| ----------- | --------------------------------------------------------------- | -------------------- |
| Attachments | List<[LTools.Office.Model.OMailAttachment](omailattachment.md)> | Вложения             |
| Body        | String                                                          | Текст тела письма    |
| From        | String                                                          | От кого              |
| ID          | String                                                          | Идентификатор письма. Позволяет обратиться к конкретному сообщению. Получить ID можно при считывании писем с помощью соответствующих элементов Студии. Например, при использовании [**Чтения почты**](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/els_outlook/el_outlook_readmail), в результате которого мы получаем список писем, у каждого из которых есть свой ID |
| MailFormat  | [LTools.Office.Model.OMailMessage.MailFormats](mailformats.md)  | Формат письма        |
| ReceiveDate | [DateTime](https://learn.microsoft.com/ru-ru/dotnet/api/system.datetime?view=netframework-4.8) | Дата и время получения письма |
| Subject     | String                                                          | Тема письма          |
| To          | List\<String>                                                   | Кому (для входящих)  |


