# Установить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (13).png>)

![](<../../../../.gitbook/assets/image (342).png>)

**Eng:** Set Credentials

Элемент позволяет добавить [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) с типом Credentials (учетные данные) в Оркестратор. 

Для успешной работы должна быть настроена связь Студии и Оркестратора. О том, как подключиться к Оркестратору, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).

### Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство       | Тип    | Описание                                                                                                     |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| Наименование\* | String | Наименование ресурса для отображения в Оркестраторе. Пример: `"My cred"`                                     |
| Логин\*        | String | Логин, который нужно установить для учетной записи. Пример: `"login"`                                        |
| Пароль\*       | String | Пароль от учетной записи. Пример: `"pass"`                                                                   |
| Таймаут        | Int32  | Лимит времени операции в миллисекундах. По умолчанию `5000`. Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой |

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

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
