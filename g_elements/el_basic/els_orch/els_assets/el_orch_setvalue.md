---
description: Set asset
---

# Установить значение

Элемент обращается в Оркестратор, чтобы установить новое значение [ресурсу](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets). В свойствах элемента необходимо указать название искомого ресурса и его новое значение. 

![Элемент «Установить значение»](<../../../../.gitbook/assets/image (305).png>)

Ресурс может иметь следующие типы данных:
* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

:small_orange_diamond: ***Чтобы изменить значение ресурса с типом Credentials, используйте элемент [Установить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_setcredentials).***


## Начальные условия

:small_blue_diamond: Установлено [подключение](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator) Студии к Оркестратору.\
:small_blue_diamond: В Оркестраторе создан ресурс (переменная).\
:small_blue_diamond: Элемент **Установить значение** можно использовать в сценарии сразу, без предварительного [Получения значения](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getvalue).


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                     |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| Наименование\* | String | Название ресурса Оркестратора, соблюдайте регистр. Пример: `"asset1"`                                                     |
| Значение\*     | Object | Значение, которое вы хотите присвоить ресурсу                                                                |
| Таймаут        | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, робот закончит работу с ошибкой. По умолчанию `5000` |


### Решение проблем

![](<../../../../.gitbook/assets1/set-asset-error-in-studio.png>)

При выполнении роботом элемента может возникнуть «Ошибка получения значения». Вероятные причины возникновения:
* ресурса с указанным названием нет в Оркестраторе;
* пользователь, который создавал ресурс в Оркестраторе, указал, что этот ресурс предназначен только для чтения.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Enterprise.OrchestratorApp.AssetSet(wf, "Key", "data");
```
{% endtab %}

{% tab title="Python" %}
```python
LTools.Enterprise.OrchestratorApp.AssetSet(wf, "Key", "data")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
_lib.LTools.Enterprise.OrchestratorApp.AssetSet(wf, "Key", "data");
```
{% endtab %}
{% endtabs %}
