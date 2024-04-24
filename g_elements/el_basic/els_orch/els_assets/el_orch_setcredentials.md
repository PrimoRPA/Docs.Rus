---
description: Set Credentials
---
# Установить учетные данные

Элемент обращается в Оркестратор, чтобы установить новое значение [ресурсу](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) с типом Credentials (учетные данные). Название ресурса указывается в свойствах элемента.

![Элемент «Установить учетные данные»](<../../../../.gitbook/assets/image (342).png>)

## Начальные условия

:small_blue_diamond: Установлено [подключение](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator) Студии к Оркестратору.\
:small_blue_diamond: В Оркестраторе создан ресурс с типом Credentials. 


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                     |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| Наименование\* | String | Название ресурса в Оркестраторе, при вводе соблюдайте регистр. Пример: `"Mycred"`                                      |
| Логин\*        | String | Логин, который нужно установить для учетной записи                                       |
| Пароль\*       | String | Пароль от учетной записи                                                                |
| Таймаут        | Int32  | Лимит времени операции в миллисекундах. По умолчанию `5000`. Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой |


### Решение проблем

![](<../../../../.gitbook/assets1/set-asset-error-in-studio.png>)

При выполнении элемента может возникнуть «Ошибка получения значения». Вероятные причины возникновения:
* ресурса с указанным названием нет в Оркестраторе;
* пользователь, который создавал ресурс в Оркестраторе, указал, что этот ресурс предназначен только для чтения.



## Только код
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
