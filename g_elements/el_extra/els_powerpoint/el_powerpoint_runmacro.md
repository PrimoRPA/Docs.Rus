# Запустить макрос

![](<../../../.gitbook/assets/image (541).png>)



Элемент, выполняющий макрос PowerPoint.

Свойства:

| Свойство     | Тип           | Описание             |
| ------------ | ------------- | -------------------- |
| Наименование | String        | Наименование макроса |
| Аргументы    | List\<object> | Аргументы макроса    |
| Результат    | object        | Результат макроса    |

{% tabs %}
{% tab title="C#" %}
```csharp
object res = app.RunMacro("mscro1", new List<object>() { 10 });
```
{% endtab %}

{% tab title="Python" %}
```python
res = app.RunMacro("mscro1", new List<object>() { 10 }) #object
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var res = app.RunMacro("mscro1", new List<object>() { 10 }); //object
```
{% endtab %}
{% endtabs %}
