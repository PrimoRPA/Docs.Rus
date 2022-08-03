# Читать адресную книгу

![](<../../../.gitbook/assets/image (48).png>)

Компонент, производящий чтение адресных книг Outlook.

| Свойство         | Тип                                                                      | Описание                                 |
| ---------------- | ------------------------------------------------------------------------ | ---------------------------------------- |
| Фильтр (e-mail)  | String                                                                   | Фильтрация по адресу почты               |
| Фильтр (имя)     | String                                                                   | Фильтрация по имени                      |
| Фильтр (фамилия) | String                                                                   | Фильтрация по фамилии                    |
| Переменная\*     | List<[LTools.Office.Model.OContact](../els\_mail/datatypes/ocontact.md)> | Переменная для хранения списка контактов |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
List<LTools.Office.Model.OContact> ret = app.ReadAddressBook("mail", "first name", "last name");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
ret = app.ReadAddressBook("mail", "first name", "last name")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
var ret = app.ReadAddressBook("mail", "first name", "last name");
```
{% endtab %}
{% endtabs %}

