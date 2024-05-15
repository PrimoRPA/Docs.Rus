---
description: Select range
---


# Выделение диапазона

Элемент выделяет диапазон ячеек Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

![](<../../../.gitbook/assets1/WFSelectRange.png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание                           |
| --------------- | ------ | ---------------------------------- |
| Диапазон\*      | String | Диапазон считывания ячеек. Пример: `"A1:D12"` |
| Страница        | String | Наименование страницы. Пример: `"Лист1"`              |
| Индекс страницы | Int32  | Номер страницы. Нумерация начинается с нуля.  Если указано название страницы, номер можно пропустить. Пример: `0`  |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SelectRange("A1:C12", "Лист1", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SelectRange("A1:C12", "Лист1", 0)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SelectRange("A1:C12", "Лист1", 0);
```
{% endtab %}
{% endtabs %}
