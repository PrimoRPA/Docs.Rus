---
description: Read mail (MS Exchange)
---


# Чтение почты


![](<../../../../.gitbook/assets/image (324).png>)

Компонент вычитывает электронную почту из MS Exchange.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство             | Тип                                                                    | Описание                                         |
| -------------------- | ---------------------------------------------------------------------- | ------------------------------------------------ |
|**Вывод**           |      |                                                                     |
| Переменная\*         | List<[LTools.Office.Model.OMailMessage](../datatypes/omailmessage.md)> | Переменная вывода для сохранения списка полученных писем |
| **Exchange**   | |
| Путь к папке         | String                                                                 | Папка, из которой будет происходить чтение писем. Например, можно выбрать папку "Входящие", "Отправленные" и т.д.. Пример: `"Inbox"`      |
| Только непрочитанные | Boolean                                                                | Загрузить только те письма, которые помечены как непрочитанные. |
| Кол-во               | Int32                                                                  | Количество писем, которые нужно загрузить. По умолчанию `30` писем |
| Направление          | |Направление сортировки (Ascending/Descending). Если установлено `Descending`, то письма будут сортироваться в порядке убывания (например, от самых новых к старым).
| Вложения             | Boolean                                                                | Определяет, нужно ли получать вложения из писем  |
| Запрос               | String                                                                 | Запрос для фильтрации писем  |
| Общий ящик           | String                                                                 | Укажите адрес [общего почтового ящика](https://learn.microsoft.com/ru-ru/exchange/collaboration/shared-mailboxes/shared-mailboxes?view=exchserver-2019). Пример:  `"info@company.com"` |
|Сортировать||***Функция сортировки доступна с версии 1.24.8***

### Свойства сортировки:
- *Сортировать*: это свойство позволяет задать критерий сортировки для получаемых писем.
  - *None*: без сортировки. Письма будут загружены в порядке их поступления.
  - *By Received Date*: сортировка писем по дате получения. Самый распространённый метод, полезен для работы с последними или старыми письмами.
  - *Bcc*: сортировка по скрытой копии (Blind Carbon Copy), используется для фильтрации писем, в которых текущий пользователь был скрытым получателем.
  - *Cc*: сортировка по получателям, добавленным в копию письма (Carbon Copy).
  - *From*: сортировка по отправителю письма.
  - *To*: сортировка по основным получателям письма.
  - *Subject*: сортировка по теме письма.
  - *Categories*: сортировка по категориям, если письма были классифицированы пользователем.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.MSExchangeApp app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
List<LTools.Office.Model.OMailMessage> msg = app.ReadMail("Inbox", true, false, 10);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.MSExchangeApp.InitSvc(wf, Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain")
msg = app.ReadMail("Inbox", True, False, 10)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.MSExchangeApp.InitSvc(wf, _lib.Microsoft.Exchange.WebServices.Data.ExchangeVersion.Exchange2013_SP1, "server url", "login", "pass", "domain");
var msg = app.ReadMail("Inbox", true, false, 10);
```
{% endtab %}
{% endtabs %}



