# Установить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (48).png>)

![](<../../../../.gitbook/assets/image (305).png>)

**Установить значение (Set asset)** - производит установку значения в Оркестратор. Под значением подразумевается новый [ресурс](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) (asset), который необходимо создать в Оркестраторе. 

Допустимые типы данных ресурса:

* String
* Integer
* Floating
* Boolean
* DateTime
* JObject (для JSON)

:bangbang: ***Чтобы создать ресурс с типом Credentials, используйте элемент [Установить учетные данные](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_orch/els_assets/el_orch_setcredentials).***

Для успешной работы обязательно должна быть настроена связь Студии и Оркестратора. О том, как подключиться к Оркестратору, см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/settings#orkestrator).

### Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство       | Тип    | Описание                                                                                                     |
| -------------- | ------ | ------------------------------------------------------------------------------------------------------------ |
| Наименование\* | String | Наименование ресурса. Пример: `"asset1"`                                                                     |
| Значение\*     | Object | Устанавливаемое значение                                                                                     |
| Таймаут        | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой |

### Только код
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
