---
description: Insert rows
---

# Вставка строк

Элемент добавляет строки в лист Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

Если в файле требуется сохранить изменения, то дополнительно используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![Элемент «Вставка строк»](<../../../.gitbook/assets1/WFInsertRows.png>)


## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание                                                                                                        | Пример    | 
| --------------- | ------ | --------------------------------------------------------------------------------------------------------------- | --------- | 
| Кол-во\*        | Int32  | Количество новых строк                                                                                          | `1`       | 
| Индекс          | Int32  | Номер строки, после которой добавится новая. Если номер не указан, то строка добавится в конце листа            | `1`       | 
| Страница        | String | Наименование страницы в книге Excel                                                                             | `"Лист1"` | 
| Индекс страницы | Int32  | Порядковый номер страницы в книге Excel, нумерация начинается с нуля. Если указан индекс, то страница в файле может быть переименована | `0`     | 

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//rowIdx - Индекс строки: [Int32] Индекс строки
//count - Количество: [Int32] Количество строк для вставки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\rows.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
Int32 rowIdx=3;
Int32 count = 2;
app.InsertRows(rowIdx,count,"Лист2",1);
app.Save();
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Кол-во: [Int32] Кол-во вставляемых строк
#index - Индекс: [Int32] Индекс строки, после которой будет производиться вставка. Если не указан, то вставка производится в конце листа
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
app = LTools.Office.ExcelApp.Init(wf, ".\\rows.xlsx",";", LTools.Office.Model.InteropTypes.DX)
rowIdx = 3;
count = 2;
app.InsertRows(rowIdx,count,"Лист2",1)
app.Save();
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Кол-во: [Int32] Кол-во вставляемых строк
//index - Индекс: [Int32] Индекс строки, после которой будет производиться вставка. Если не указан, то вставка производится в конце листа
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\rows.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var rowIdx = 3;
var count = 2;
app.InsertRows(rowIdx, count, "Лист2",1);
app.Save();
```
{% endtab %}
{% endtabs %}
