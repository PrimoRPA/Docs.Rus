# Запустить макрос

![](<../../../../.gitbook/assets/image (810).png>)

Элемент, выполняющий макрос Таблицы.

| Свойство     | Тип    | Описание                     |
| ------------ | ------ | ---------------------------- |
| Наименование | String | Наименование макроса         |
| Переменная   | Object | Результат выполнения скрипта |

{% tabs %}
{% tab title="C#" %}
```csharp
app.RunMacro("MacroName");
```
{% endtab %}

{% tab title="Python" %}
```python
app.RunMacro("MacroName")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.RunMacro("MacroName");
```
{% endtab %}
{% endtabs %}

