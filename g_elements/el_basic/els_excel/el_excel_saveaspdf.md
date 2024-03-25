---
description: Save as PDF
---

# Сохранить как PDF

Элемент экспортирует книгу Excel в формат PDF. Путь до экспортируемого файла и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

![](<../../../.gitbook/assets1/WFExcelToPdf.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство                  | Тип     | Описание                                                                                                                                     | Пример    |
| ------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| Путь                      | String  | Путь до места сохранения PDF-файла                                                                                                           | `@"С:\folder\file.pdf"` |
| Заменять существующий     | Boolean | Определяет, нужно ли пересохранить уже существующий файл PDF. По умолчанию чекбокс не установлен — файл не пересохраняется                   |  |
| Индекс первой страницы    | Int32   | Номер первой страницы для экспорта. Нумерация начинается с нуля                                                                              | `0` |
| Индекс последней страницы | Int32   | Номер последней страницы для экспорта                                                                                                        | `2` |
| Мин. качество             | Boolean | Определите качество выходного файла. При установке этого чекбокса файл сохранится в минимальном качестве (для онлайн-публикации). По умолчанию чекбокс снят — файл сохраняется в стандартном качестве (для онлайн-публикации и печати) |  |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, @"c:\file.xlsx");
app.ExportToPdf(@"c:\file.pdf", true, false)
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "c:\file.xlsx")
app.ExportToPdf("c:\file.pdf", true, false
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "c:\\file.xlsx");
app.ExportToPdf("c:\\file.pdf", true, false);
```
{% endtab %}
{% endtabs %}
