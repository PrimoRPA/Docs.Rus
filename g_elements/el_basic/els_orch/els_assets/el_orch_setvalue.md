# Установить значение

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (93).png>)

![](<../../../../.gitbook/assets/image (305).png>)

Компонент, производящий установку значения в оркестратор

| Свойство       | Тип    | Описание                 |
| -------------- | ------ | ------------------------ |
| Наименование\* | String | Наименование значения    |
| Значение\*     | Object | Устанавливаемое значение |

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
