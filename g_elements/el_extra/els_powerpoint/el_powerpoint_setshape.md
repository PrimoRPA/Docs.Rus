# Редактировать фигуру

![](<../../../.gitbook/assets/image (480).png>)



Компонент, производящий редактирование фигуры презентации.

Свойства

| Свойство         | Тип                                        | Описание                            |
| ---------------- | ------------------------------------------ | ----------------------------------- |
| Индекс слайда    | Int32                                      | Индекс слайда                       |
| Фигура           | String                                     | Имя фигуры для редактирования       |
| Менять положение | Boolean                                    | Признак изменения положения в слоях |
| Тип положения    | Primo.Office.PowerPoint. Model.ShapeZOrder | Тип изменения положения в слоях     |
| Размер           | [double](https://learn.microsoft.com/ru-ru/dotnet/api/system.double?view=net-5.0&viewFallbackFrom=windowsdesktop-3.0)   | Размер шрифта |

{% tabs %}
{% tab title="C#" %}
```csharp
app.SetShapeZOrder(1, "Shape1", Primo.Office.PowerPoint. Model.ShapeZOrder.BringToFront);
app.SetShapeFont(2, "Shape2", 12);
```
{% endtab %}

{% tab title="Python" %}
```python
app.SetShapeZOrder(1, "Shape1", Primo.Office.PowerPoint. Model.ShapeZOrder.BringToFront)
app.SetShapeFont(2, "Shape2", 12)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
app.SetShapeZOrder(1, "Shape1", _lib.Primo.Office.PowerPoint. Model.ShapeZOrder.BringToFront)
app.SetShapeFont(2, "Shape2", 12)
```
{% endtab %}
{% endtabs %}
