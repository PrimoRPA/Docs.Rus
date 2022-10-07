# Получить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (210).png>)

![](<../../../../.gitbook/assets/image (270).png>)

Компонент, производящий получение учетных данных из оркестратора

| Свойство       | Тип                          | Описание                                   |
| -------------- | ---------------------------- | ------------------------------------------ |
| Наименование\* | String                       | Наименование значения                      |
| Логин          | String                       | Переменная для хранения полученного логина |
| Пароль         | System.Security.SecureString | Переменная для хранения полученного пароля |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.Model.CredentialResult ret = LTools.Enterprise.OrchestratorApp.CredentialsGet(wf, "Key");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.CredentialsGet(wf, "Key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.CredentialsGet(wf, "Key");
```
{% endtab %}
{% endtabs %}
