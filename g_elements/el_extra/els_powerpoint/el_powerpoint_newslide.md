# Добавить слайд

![](<../../../.gitbook/assets/image (464).png>)



Компонент, добавляющий новый слайд в презентацию.

Свойства

|              |        |                                                     |
| ------------ | ------ | --------------------------------------------------- |
| Индекс       | Int32  | Индекс вставки. Если не указан, добавляется в конец |
| Дизайн       | String | Дизайн слайда                                       |
| Тема         | String | Тема оформления слайда                              |
| Новый индекс | Int32  | Индекс нового слайда                                |

{% tabs %}
{% tab title="C#" %}
```csharp
int newidx = app.AddNewSlide(1, "LayoutText", "Default");
```
{% endtab %}

{% tab title="Python" %}
```python
newidx = app.AddNewSlide(1, "LayoutText", "Default") #int
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var newidx = app.AddNewSlide(1, "LayoutText", "Default"); //int
```
{% endtab %}
{% endtabs %}
