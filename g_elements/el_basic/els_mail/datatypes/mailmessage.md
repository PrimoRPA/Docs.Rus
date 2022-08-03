# MailMessage

LTools.Network.Model.EMail.MailMessage

| Свойство    | Тип                                        | Описание                |
| ----------- | ------------------------------------------ | ----------------------- |
| UID         | String                                     | Идентификатор сообщения |
| Subject     | String                                     | Тема письма             |
| From        | List\<String>                              | От кого                 |
| To          | List\<String>                              | Кому                    |
| CC          | List\<String>                              | Копия                   |
| Date        | DateTime?                                  | Дата письма             |
| TextBody    | String                                     | Тело письма (текст)     |
| HtmlBody    | String                                     | Тело письма (HTML)      |
| Attachments | List<[MailAttachment](mailattachments.md)> | Вложения                |

