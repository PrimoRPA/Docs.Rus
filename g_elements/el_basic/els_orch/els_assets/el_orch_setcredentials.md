# Установить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (233).png>)

![](<../../../../.gitbook/assets/image (342).png>)

Компонент, производящий установку учетных данных в оркестратор

| Свойство       | Тип    | Описание              |
| -------------- | ------ | --------------------- |
| Наименование\* | String | Наименование значения |
| Логин\*        | String | Логин                 |
| Пароль\*       | String | Пароль                |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.CredentialsSet(wf, "Key", "login", "password");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.CredentialsSet(wf, "Key", "login", "password")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Enterprise.OrchestratorApp.CredentialsSet(wf, "Key", "login", "password");
```
{% endtab %}
{% endtabs %}
