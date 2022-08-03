# Переименовать страницу

![](<../../../../../.gitbook/assets/image (512).png>)

Компонент, переименовывающий страницу Таблицы.

| Свойство | Тип    | Описание        |
| -------- | ------ | --------------- |
| Имя      | String | Имя страницы    |
| Индекс   | Int32  | Индекс страницы |

{% tabs %}
{% tab title="C#" %}
```csharp
app.SheetRename("Page2", 4);
```
{% endtab %}

{% tab title="Python" %}
```python
app.SheetRename("Page2", 4)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SheetRename("Page2", 4);
```
{% endtab %}
{% endtabs %}
