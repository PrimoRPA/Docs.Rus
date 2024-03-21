---
description: Get Credentials
---

# Получить учетные данные

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (44).png>)

## Назначение

Элемент позволяет получить учетные данные из Оркестратора. Под учетными данными подразумевается [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) с типом Credentials, который был создан в Оркестраторе и хранится в базе данных. 

![](<../../../../.gitbook/assets/image (386).png>)

## Начальные условия

:small_blue_diamond: Установлено [подключение](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator) Студии к Оркестратору.\
:small_blue_diamond: В Оркестраторе создан ресурс (переменная) с типом Credentials. 

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип                                              | Описание                                                                                                | Пример              |
| -------------- | ------------------------------------------------ | ------------------------------------------------------------------------------------------------------- | ------------------- |
| **Процесс:**  |    |  |
| Наименование\* | String                                           | Имя ресурса с учетными данными, значение которого хотите получить. Должно совпадать с названием ресурса в Оркестраторе. При вводе соблюдайте регистр | `"MyCred"` |
| Таймаут        | Int32                                            | Лимит времени операции, задается в миллисекундах. По умолчанию `5000`. Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой | `5000`   |
| **Вывод:**   |   |   |
| Логин          | String                                           | Название строковой переменной, в которой будет храниться логин из полученных учетных данных   |
| Пароль         | [System.Security.SecureString](https://learn.microsoft.com/ru-Ru/dotnet/api/system.security.securestring?view=net-6.0) | Название переменной для хранения полученного пароля. Пароль будет сохранен в зашифрованном виде. Впоследствии его можно использовать в других элементах Студии, обладающих свойством **Защищенный пароль**  |


### Решение проблем

![](<../../../../.gitbook/assets1/set-asset-error-in-studio.png>)

При выполнении элемента может возникнуть «Ошибка получения значения». Она возникает, если ресурса с указанным названием нет в Оркестраторе.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.Model.CredentialResult ret = LTools.Enterprise.OrchestratorApp.CredentialsGet(wf, "MyCred");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.CredentialsGet(wf, "MyCred")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.CredentialsGet(wf, "MyCred");
```
{% endtab %}
{% endtabs %}
