# Приложение Outlook

![](<../../../.gitbook/assets/image (892).png>)

Компонент, производящий подключение к Outlook.

| Свойство    | Тип    | Описание                      |
| ----------- | ------ | ----------------------------- |
| Имя профиля | String | Имя профиля Outlook (Outlook) |
| Пароль      | String | Пароль профиля Outlook        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.OutlookApp app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.OutlookApp.Init(wf, "Outlook", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.OutlookApp.Init(wf, "Outlook", "password");
```
{% endtab %}
{% endtabs %}
