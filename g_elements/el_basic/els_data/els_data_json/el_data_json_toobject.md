# JSON к объекту

![](<../../../../.gitbook/assets/image (119) (54).png>)

![](<../../../../.gitbook/assets/image (255).png>)

Компонент, осуществляющий преобразование JSON в объект.

| Свойство     | Тип     | Описание                                                                                                                                                                |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Переменная\* | dynamic | Переменная, получающая результирующий объект '[https://www.newtonsoft.com/json/help/html/Introduction.htm](https://www.newtonsoft.com/json/help/html/Introduction.htm)' |
| Данные\*     | String  | Строка JSON                                                                                                                                                             |

{% tabs %}
{% tab title="C#" %}
```csharp
dynamic ret = Newtonsoft.Json.JsonConvert.DeserializeObject("json");
```
{% endtab %}

{% tab title="Python" %}
```python
ret = Newtonsoft.Json.JsonConvert.DeserializeObject("json")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.Newtonsoft.Json.JsonConvert.DeserializeObject("json");
```
{% endtab %}
{% endtabs %}
