# Получить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (234).png>)

![](<../../../../.gitbook/assets/image (269).png>)

Компонент позволяет получить значения из Оркестратора.

| Свойство       | Тип    | Описание                                   |
| -------------- | ------ | ------------------------------------------ |
| Наименование\* | String | Укажите имя переменной (ресурса) из Оркестратора |
| Результат      | - | Переменная для хранения полученного текста. Имеет такой же тип данных, как и значение [ресурса](https://docs.primo-rpa.ru/primo-rpa/orchestrator/basics/assets) в Оркестраторе. Например, Int или String |

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
