# Получить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (19).png>)

![](<../../../../.gitbook/assets/image (269).png>)

Компонент позволяет получить значение из Оркестратора.

| Свойство       | Тип    | Описание                                                                                                                                             |
| -------------- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------- |
| Наименование\* | String | Укажите имя переменной ([ресурса](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets)) из Оркестратора, значение которой хотите получить |
| Таймаут        | Int32  | Лимит времени операции (мс). Если по истечении лимита операция не выполнена, Робот закончит работу с ошибкой                                         |
| Результат      | -      | Переменная для сохранения полученного текста. Имеет такой же тип данных, как и значение ресурса в Оркестраторе. Например, Int или String             |

{% tabs %}
{% tab title="C#" %}
```csharp
object ret = LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.AssetGet(wf, "Key");
```
{% endtab %}
{% endtabs %}
