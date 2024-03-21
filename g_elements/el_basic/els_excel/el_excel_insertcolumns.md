---
description: Insert columns
---

# Вставка колонок

Элемент вставляет колонки в лист Excel.

Путь до файла, тип драйвера и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). Если в файле требуется сохранить изменения, то после вставки колонок используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![](<../../../.gitbook/assets1/WFInsertColumns.png>)

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание                                                                                                             | Пример     |
| --------------- | ------ | -------------------------------------------------------------------------------------------------------------------- | ---------- |
| **Excel:**      |        |                                                                                                                      |            |     
| Кол-во\*        | Int32  | Количество ставляемых колонок                                                                                        | `1`        |
| Индекс          | Int32  | Порядковый номер колонки, **слева** от которой добавится новая. Нумерация начинается с нуля. Если номер не указан, то вставка выполнится в конце листа | `0` |
| Страница        | String | Наименование страницы                                                                                                | "Лист1"    |
| Индекс страницы | Int32  | Порядковый номер страницы Excel, нумерация начинается с нуля                                                         | `0`        |

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//columnIdx - Индекс колонки: [Int32] Индекс колонки
//count - Количество: [Int32] Количество колонок для вставки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\columns.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
Int32 columnIdx=3;
Int32 count = 2;
app.InsertColumns(columnIdx,count,"Лист1",0);
app.Save();
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Кол-во: [Int32] Кол-во ставляемых колонок
#index - Индекс: [Int32] Индекс колонки, слева от которой будет производиться вставка. Если не указан, то вставка производится в конце листа
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
app = LTools.Office.ExcelApp.Init(wf, ".\\columns.xlsx",";", LTools.Office.Model.InteropTypes.DX)
columnIdx = 3;
count = 2;
app.InsertColumns(columnIdx,count,"Лист1",0)
app.Save();
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Кол-во: [Int32] Кол-во ставляемых колонок
//index - Индекс: [Int32] Индекс колонки, слева от которой будет производиться вставка. Если не указан, то вставка производится в конце листа
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\columns.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var columnIdx = 3;
var count = 2;
app.InsertColumns(columnIdx, count, "Лист1",0);
app.Save();
```
{% endtab %}
{% endtabs %}


