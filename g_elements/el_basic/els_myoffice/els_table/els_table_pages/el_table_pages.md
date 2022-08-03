# Список страниц

![](<../../../../../.gitbook/assets/image (582).png>)

Компонент, получающий список страниц Таблицы.

| Свойство   | Тип           | Описание                               |
| ---------- | ------------- | -------------------------------------- |
| Переменная | List\<String> | Переменная для хранения списка страниц |

{% tabs %}
{% tab title="C#" %}
```csharp
List<string> sheets = app.GetSheets();
```
{% endtab %}

{% tab title="Python" %}
```python
sheets = app.GetSheets() #List<string>
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
let sheets = app.GetSheets(); //List<string>
```
{% endtab %}
{% endtabs %}
