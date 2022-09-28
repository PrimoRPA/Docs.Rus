# Объект к JSON

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (263).png>)

![](<../../../../.gitbook/assets/image (285).png>)

Компонент, осуществляющий преобразование JSON в объект.

| Свойство     | Тип     | Описание                                                                                                                                                                |
| ------------ | ------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Переменная\* | dynamic | Переменная, получающая результирующий объект '[https://www.newtonsoft.com/json/help/html/Introduction.htm](https://www.newtonsoft.com/json/help/html/Introduction.htm)' |
| Данные\*     | String  | Строка JSON                                                                                                                                                             |

{% tabs %}
{% tab title="C#" %}
```csharp
string ret = Newtonsoft.Json.JsonConvert.SerializeObject(obj);
```
{% endtab %}

{% tab title="Python" %}
```python
ret = Newtonsoft.Json.JsonConvert.SerializeObject(obj)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var ret = _lib.Newtonsoft.Json.JsonConvert.SerializeObject(obj);
```
{% endtab %}
{% endtabs %}
