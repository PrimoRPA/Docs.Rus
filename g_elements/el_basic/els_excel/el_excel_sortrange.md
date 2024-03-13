---
description: Sort range
---

# Сортировка диапазона

Элемент устанавливает сортировку диапазона ячеек Excel.

![](<../../../.gitbook/assets/image (336).png>)

**Примечания**:

1. Путь до файла, тип драйвера и другие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, используйте дополнительно элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save). Автоматически изменения не сохраняются.



## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип                                 | Описание                                                                               | Пример   |
| --------------- | ----------------------------------- | -------------------------------------------------------------------------------------- | -------- |
| Диапазон\*      | String                              | Диапазон считывания ячеек. Пример: `"A2:A12"`. Если диапазон не указан, будет отсортирован выделенный диапазон | `"A2:A12"` |
| Направление\*   | LTools.Office.Model. SortDirections | Направление сортировки: по возрастанию (ascending) или по убыванию (descending). По умолчанию используется сортировка по возрастанию | `Ascending` | 
| Страница        | String                              | Наименование страницы Excel                                   | `"Персонал"` | 
| Индекс страницы | Int32                               | Порядковый номер страницы                                        | `0` |



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
