# Удалить слайд

![](<../../../.gitbook/assets/image (931).png>)



Компонент, удаляющий слайд из презентации.

Свойства

| Свойство | Тип   | Описание                                         |
| -------- | ----- | ------------------------------------------------ |
| Индекс   | Int32 | Индекс слайда. Если не указан, удаляет последний |

{% tabs %}
{% tab title="C#" %}
```csharp
app.DeleteSlide(4);
```
{% endtab %}

{% tab title="Python" %}
```python
app.DeleteSlide(4)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.DeleteSlide(4);
```
{% endtab %}
{% endtabs %}
