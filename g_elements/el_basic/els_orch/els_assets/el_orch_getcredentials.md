# Получить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (210).png>)

![](<../../../../.gitbook/assets/image (270).png>)

Компонент, производящий получение учетных данных из Оркестратора. Для этого в Оркестраторе должен быть создан [ресурс с типом Сredentials](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) и настроена связь Студии и Оркестратора.

| Свойство       | Тип                          | Описание                                   |
| -------------- | ---------------------------- | ------------------------------------------ |
| ***Общие***    |    | Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements) |
| ***Процесс***  |    |  |
| Наименование\* | String                       | Укажите имя переменной в Оркестраторе, значение которой хотите получить |
| Таймаут        | Int32                        | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |
| ***Вывод***  |    |  |
| Логин          | String                       | Укажите переменную для хранения полученного логина |
| Пароль         | [System.Security.SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=net-6.0) | Укажите переменную для хранения полученного пароля. Пароль будет сохранен в зашифрованном виде. Впоследствии его можно будет указывать в свойстве **Защищенный пароль** элементов, использующих пароли |

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
