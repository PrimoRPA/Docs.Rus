# Удалить страницу

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (139).png>)

![](<../../../../.gitbook/assets/image (47).png>)

Компонент удаляет страницу Excel.

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство | Тип   | Описание        |
| -------- | ----- | --------------- |
| Индекс\* | Int32 | Индекс страницы - порядковый номер страницы, которую нужно удалить. Отсчет с 0. Пример: `0` - в этом случае будет удалена первая страница |
| Имя\*   | String | Название страницы Excel, которую нужно удалить |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SheetDelete(1);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SheetDelete(1)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SheetDelete(1);
```
{% endtab %}
{% endtabs %}
