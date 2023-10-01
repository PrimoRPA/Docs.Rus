# Получить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (44).png>)

![](<../../../../.gitbook/assets/image (386).png>)

**Eng:** Get Credentials

Элемент позволяет получить учетные данные из Оркестратора. Под учетными данными подразумевается [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) с типом Credentials, который хранится в Оркестраторе. 

Для успешной работы должна быть настроена связь Студии и Оркестратора. О том, как подключиться к Оркестратору, читайте [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство       | Тип                                                                                                                    | Описание                                                                                                                                                                                               |
| -------------- | ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| _**Процесс:**_  |    |  |
| Наименование\* | String                                                                                                                 | Имя ресурса с учетными данными, значение которого вы хотите получить       |
| Таймаут        | Int32                                                                                                                  | Лимит времени операции, задается в миллисекундах. Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |
| _**Вывод:**_   |   |   |
| Логин          | String                                                                                                                 | Укажите переменную для хранения полученного логина из учетных данных   |
| Пароль         | [System.Security.SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=net-6.0) | Укажите переменную для хранения полученного пароля. Пароль будет сохранен в зашифрованном виде. Впоследствии его можно будет использовать в других элементах Студии, обладающих свойством **Защищенный пароль**  |

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
