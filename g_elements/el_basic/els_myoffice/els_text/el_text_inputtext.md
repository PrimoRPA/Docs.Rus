# Ввод текста

![](<../../../../.gitbook/assets/image (579).png>)

Компонент, производящий запись данных в документ Текст.

| Свойство | Тип    | Описание                                                                                      |
| -------- | ------ | --------------------------------------------------------------------------------------------- |
| Закладка | String | Имя закладки, определяющей начало записи. Если не указано, запись производится в конец текста |
| Текст    | String | Данные, вводимые в документ                                                                   |

{% tabs %}
{% tab title="C#" %}
```csharp
app.AppendText("text", bookmark);
```
{% endtab %}

{% tab title="Python" %}
```python
app.AppendText("text", bookmark)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.AppendText("text", bookmark);
```
{% endtab %}
{% endtabs %}
