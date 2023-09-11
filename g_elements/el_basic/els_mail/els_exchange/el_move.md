# Переместить в папку

![](<../../../../.gitbook/assets/image (297).png>)

Компонент, осуществляющий перемещение сообщений между папками MS Exchange.

## Свойства

Свойства элемента разделены на группы, они выделены в таблице жирным курсивом.\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство           | Тип                                                                    | Описание         |
| ------------------ | ---------------------------------------------------------------------- | ---------------- |
| ***Общие***  | | Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa) | 
| ***Exchange***  | | | 
| Папка назначения\* | String                                                                 | Папка назначения |
| Письма\*           | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Массив сообщений |
| Общий ящик         | String  | Укажите общий почтовый ящик, если письма нужно перемещать в нем |

## Только код
Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("Inbox", true, false, 10);
app.MoveToFolder(msg[0], "folder");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = app.ReadMail("Inbox", True, False, 10)
app.MoveToFolder(msg[0], "folder")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = app.ReadMail("Inbox", true, false, 10);
app.MoveToFolder(msg[0], "folder");
```
{% endtab %}
{% endtabs %}
