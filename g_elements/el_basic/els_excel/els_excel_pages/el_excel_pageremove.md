# Удалить страницу

![](<../../../../.gitbook/assets/image (47).png>)

Компонент удаляет страницу Excel по ее порядковому номеру или названию. Если изменение требуется сохранить, не забудьте в конце работы с Excel использовать элемент [**Сохранить документ**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

При удалении страницы требуется обязательно указать лишь одно из свойств: либо индекс, либо имя страницы.

| Свойство | Тип   | Описание        |
| -------- | ----- | --------------- |
| Индекс\* | Int32 | Порядковый номер страницы, которую нужно удалить. Отсчет начинается с 0. Пример: `0` - в этом случае будет удалена первая страница |
| Имя\*   | String | Название страницы Excel, которую нужно удалить. Пример: `"Отпуска"`. Если указано название, индекс можно оставить пустым |


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
