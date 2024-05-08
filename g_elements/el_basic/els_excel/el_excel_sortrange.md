---
description: Sort range
---

# Сортировка диапазона

Элемент сортирует данные в указанном диапазоне ячеек Excel. Путь до файла и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

Если в файле требуется сохранить изменения, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save). 

![](<../../../.gitbook/assets1/WFSortRange.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип                                 | Описание                                                                               | Пример   |
| --------------- | ----------------------------------- | -------------------------------------------------------------------------------------- | -------- |
| Диапазон\*      | String                              | Диапазон считывания ячеек. Пример: `"A2:A12"`. Если диапазон не указан, будет отсортирован выделенный диапазон. <p>Если в значении указать `"*"`, то данные отсортируются по первому столбцу </p>| `"A2:A12"` |
| Направление\*   | LTools.Office.Model. SortDirections | Направление сортировки: <p> 1) по возрастанию (ascending) — значение по умолчанию; </p> <p> 2) по убыванию (descending)</p>| `Ascending` | 
| Страница        | String                              | Наименование страницы Excel                                   | `"Персонал"` | 
| Индекс страницы | Int32                               | Порядковый номер страницы Excel. Нумерация начинается с нуля  | `0`          |



## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SortRange("A1:C12", LTools.Office.Model.SortDirections.ASCENDING, "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SortRange("A1:C12", LTools.Office.Model.SortDirections.ASCENDING, "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SortRange("A1:C12", _lib.LTools.Office.Model.SortDirections.ASCENDING, "Лист1");
```
{% endtab %}
{% endtabs %}
