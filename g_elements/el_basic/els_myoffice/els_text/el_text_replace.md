# Заменить текст

![](<../../../../.gitbook/assets/image (939).png>)

Заменяет все вхождения исходного текста на новый.

|                |        |                          |
| -------------- | ------ | ------------------------ |
| Исходный текст | String | Текст, подлежащий замене |
| Новый текст    | String | Новый текст              |

{% tabs %}
{% tab title="C#" %}
```csharp
app.ReplaceText("oldText", "newText");
```
{% endtab %}

{% tab title="Python" %}
```python
app.ReplaceText("oldText", "newText")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AppendText("oldText", "newText");
```
{% endtab %}
{% endtabs %}
