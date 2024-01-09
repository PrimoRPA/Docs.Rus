# Установить значение

*Eng: Set asset*

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (48).png>)

![](<../../../../.gitbook/assets/image (305).png>)

## Предварительные условия

:white_check_mark: Настроено подключение Студии к Оркестратору. О том, как это сделать, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).

:white_check_mark: В Оркестраторе создан ресурс (переменная).

## Назначение

Элемент позволяет установить значение [ресурса](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) в Оркестраторе. Для этого в свойствах элемента указываем название существующего ресурса и его новое значение. Данный элемент работает со всеми типами данных ресурса, кроме Credentials. А именно:
* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

:bangbang: ***Чтобы изменить значение ресурса с типом Credentials, используйте элемент [Установить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_setcredentials).***

Установку значения можно использовать в сценарии сразу, без предварительного этапа в виде элемента [Получить значение](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_getvalue).


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                     |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| Наименование\* | String | Наименование ресурса. Пример: `"asset1"`                                                                     |
| Значение\*     | Object | Устанавливаемое значение                                                                                     |
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
