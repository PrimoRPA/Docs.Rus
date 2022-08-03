# Чтение почты

![](<../../../../.gitbook/assets/image (434).png>)

Компонент, получающий письма из Lotus Notes.

| Свойство   | Тип                                                                    | Описание                                           |
| ---------- | ---------------------------------------------------------------------- | -------------------------------------------------- |
| Папка\*    | String                                                                 | Папка сообщений                                    |
| Вложения   | Boolean                                                                | Признак чтения вложений                            |
| Получить   | Int32                                                                  | Кол-во писем для чтения                            |
| Переменная | LTools.Network.Model.EMail.LotusInst                                   | Ссылка на подключение                              |
| Таймаут\*  | Int32                                                                  | Предельное время ожидания завершения процесса (мс) |
| Письма     | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Переменная для хранения писем                      |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.LotusApp app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
List<LTools.Office.Model.OMailMessage> mail = app.GetMail("($Inbox)", 10, false, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000)
mail = app.GetMail("($Inbox)", 10, False, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
var mail = app.GetMail("($Inbox)", 10, false, 10000);
```
{% endtab %}
{% endtabs %}
