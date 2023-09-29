# Получить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (44).png>)

![](<../../../../.gitbook/assets/image (386).png>)

**Eng:** Get Credentials

Компонент, производящий получение учетных данных из Оркестратора. Для этого в Оркестраторе должен быть создан [ресурс с типом Сredentials](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) и настроена связь Студии и Оркестратора.

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство       | Тип                                                                                                                    | Описание                                                                                                                                                                                               |
| -------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |

| _**Процесс:**_  |                                                                                                                        |                                                                                                                                                                                                        |
| Наименование\* | String                                                                                                                 | Укажите имя переменной в Оркестраторе, значение которой хотите получить                                                                                                                                |
| Таймаут        | Int32                                                                                                                  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой                                                                                           |
| _**Вывод:**_    |                                                                                                                        |                                                                                                                                                                                                        |
| Логин          | String                                                                                                                 | Укажите переменную для хранения полученного логина                                                                                                                                                     |
| Пароль         | [System.Security.SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=net-6.0) | Укажите переменную для хранения полученного пароля. Пароль будет сохранен в зашифрованном виде. Впоследствии его можно будет указывать в свойстве **Защищенный пароль** элементов, использующих пароли |

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
