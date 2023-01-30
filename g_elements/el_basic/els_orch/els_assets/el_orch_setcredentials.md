# Установить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (146).png>)

![](<../../../../.gitbook/assets/image (342).png>)

Компонент, производящий установку учетных данных в Оркестратор.

| Свойство       | Тип    | Описание              |
| -------------- | ------ | --------------------- |
| Наименование\* | String | Наименование значения |
| Логин\*        | String | Логин                 |
| Пароль\*       | String | Пароль                |
| Таймаут        | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |

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
