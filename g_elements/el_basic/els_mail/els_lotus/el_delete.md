# Удалить сообщения

![](<../../../../.gitbook/assets/image (260).png>)

Компонент, удаляющий письма из Lotus Notes.

| Свойство   | Тип                                                                    | Описание                                           |
| ---------- | ---------------------------------------------------------------------- | -------------------------------------------------- |
| Папка\*    | String                                                                 | Папка сообщений                                    |
| Переменная | LTools.Network.Model.EMail.LotusInst                                   | Ссылка на подключение                              |
| Таймаут\*  | Int32                                                                  | Предельное время ожидания завершения процесса (мс) |
| Сообщение  | [LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)       | Удаляемое сообщение                                |
| Список     | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Список удаляемых сообщений                         |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.LotusApp app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
List<LTools.Office.Model.OMailMessage> mail = app.GetMail("($Inbox)", 10, false, 10000);
app.DeleteMail(mail[0], "($Inbox)", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000)
mail = app.GetMail("($Inbox)", 10, False, 10000)
app.DeleteMail(mail[0], "($Inbox)", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
var mail = app.GetMail("($Inbox)", 10, false, 10000);
app.DeleteMail(mail[0], "($Inbox)", 10000);
```
{% endtab %}
{% endtabs %}
