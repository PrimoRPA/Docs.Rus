# Сохранить сообщение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (252).png>)

![](<../../../../.gitbook/assets/Сохранить сообщение Exchange и Outlook.png>)

Позволяет сохранить на диск письмо из электронной почты MS Exchange. Корректно работает только внутри контейнера [**Сервер MS Exchange**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_mail/els\_exchange/el\_connect).

> _Общие свойства элемента описаны в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)_._

| Свойство    | Тип                                                                        | Описание                               |
| ----------- | -------------------------------------------------------------------------- | -------------------------------------- |
| Путь\*      | String                                                                     | Путь сохранения файла в формате \*.eml |
| Сообщение\* | [LTools.Office.Model.OMailMessage](../els\_mail/datatypes/omailmessage.md) | Письмо для сохранения, переменная      |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "URL", "login", "pass", "domain");
app.SaveMessage(msg, @"C:\file.eml");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "URL", "login", "pass", "domain")
app.SaveMessage(msg, "C:\file.eml")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "URL", "login", "pass", "domain");
app.SaveMessage(msg, "C:\\file.eml");
```
{% endtab %}
{% endtabs %}
