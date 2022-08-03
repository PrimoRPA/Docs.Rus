# Переместить сообщения

![](<../../../../.gitbook/assets/image (401).png>)

Компонент, перемещающий письма между папками Lotus Notes.

| Свойство           | Тип                                                                    | Описание                                           |
| ------------------ | ---------------------------------------------------------------------- | -------------------------------------------------- |
| Папка назначения\* | String                                                                 | Папка назначения сообщений                         |
| Переменная         | LTools.Network.Model.EMail.LotusInst                                   | Ссылка на подключение                              |
| Таймаут\*          | Int32                                                                  | Предельное время ожидания завершения процесса (мс) |
| Сообщение          | [LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)       | Перемещаемое сообщение                             |
| Список             | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Список перемещаемых сообщений                      |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.LotusApp app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
List<LTools.Office.Model.OMailMessage> mail = app.GetMail("($Inbox)", 10, false, 10000);
app.MoveToFolder(mail[0], "folder", 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000)
mail = app.GetMail("($Inbox)", 10, False, 10000)
app.MoveToFolder(mail[0], "folder", 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
var mail = app.GetMail("($Inbox)", 10, false, 10000);
app.MoveToFolder(mail[0], "folder", 10000);
```
{% endtab %}
{% endtabs %}
