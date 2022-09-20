# Получить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (2) (75).png>)

![](<../../../../.gitbook/assets/image (269).png>)

Компонент, производящий получение значения из оркестратора

| Свойство       | Тип    | Описание                                   |
| -------------- | ------ | ------------------------------------------ |
| Наименование\* | String | Наименование значения                      |
| Результат      | Object | Переменная для хранения полученного текста |

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
