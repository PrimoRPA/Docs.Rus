# Документ Google Sheets

![](<../../../.gitbook/assets/image (289).png>)

Компонент, производящий подключение к документу Google Sheets.

| Свойство       | Тип    | Описание                   |
| -------------- | ------ | -------------------------- |
| Путь к файлу\* | String | Путь к файлу авторизации   |
| ID документа\* | String | ID документа Google Sheets |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.GoogleSheetsApp app = LTools.Office.GoogleSheetsApp.Init(wf, @"Путь к токену", @"ID документа");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.GoogleSheetsApp.Init(wf, "Путь к файлу токена", "ID документа")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let app = _lib.LTools.Office.GoogleSheetsApp.Init(wf, "Путь к файлу токена", "ID документа");
```
{% endtab %}
{% endtabs %}
