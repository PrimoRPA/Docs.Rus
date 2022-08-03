# Должен остановиться

![](<../../../../.gitbook/assets/image (777).png>)

![](<../../../../.gitbook/assets/image (282).png>)



Компонент, получающий сигнал остановки из оркестратора.

| Свойство    | Тип     | Описание                                  |
| ----------- | ------- | ----------------------------------------- |
| Результат\* | Boolean | Переменная для хранения полученных данных |

{% tabs %}
{% tab title="C#" %}
```csharp
bool ret = LTools.Enterprise.OrchestratorApp.ShouldStop(wf);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = LTools.Enterprise.OrchestratorApp.ShouldStop(wf)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.LTools.Enterprise.OrchestratorApp.ShouldStop(wf);
```
{% endtab %}
{% endtabs %}
