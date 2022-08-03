# Отправить письмо

![](<../../../../.gitbook/assets/image (306).png>)

Компонент, осуществляющий отправку почтового сообщения Lotus Notes.

| Свойство        | Тип                                   | Описание                                           |
| --------------- | ------------------------------------- | -------------------------------------------------- |
| Переменная      | LTools.Network.Model.EMail. LotusInst | Ссылка на подключение                              |
| Кому\*          | String                                | Адресат - Кому                                     |
| Копия\*         | String                                | Копия                                              |
| Скрытая копия\* | String                                | Скрытая копия                                      |
| Тема            | String                                | Тема сообщения                                     |
| Содержимое\*    | String                                | Содержимое сообщения                               |
| HTML            | Boolean                               | Признак HTML-содержимого сообщения                 |
| Таймаут\*       | Int32                                 | Предельное время ожидания завершения процесса (мс) |
| Вложения        | List\<String>                         | Вложения                                           |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.LotusApp app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
app.Send("to", "cc", "bcc", "subject", "body", new List<string>() { "file1" }, true, 10000);
```
{% endtab %}

{% tab title="Python" %}
```python
dt = List[String]()
dt.Add("file1")
app = LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000)
app.Send("to", "cc", "bcc", "subject", "body", dt, True, 10000)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.String));
lst.Add("file 1");
var app = _lib.LTools.Office.LotusApp.Init(wf, "server", "db file", "password", 10000);
app.Send("to", "cc", "bcc", "subject", "body", lst, true, 10000);
```
{% endtab %}
{% endtabs %}

