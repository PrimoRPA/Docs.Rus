---
description: Delete rows
---


# Удаление строк

Элемент удаляет выбранные строки из листа Excel.

Путь до файла, тип драйвера и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). Чтобы сохранить изменения, используйте также элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save). 

![](<../../../.gitbook/assets1/WFDeleteRows.png>)

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание                                                    | Пример    |
| --------------- | ------ | ----------------------------------------------------------- | --------- |
| Кол-во\*        | Int32  | Количество удаляемых строк                                  | `1`       |
| Индекс\*        | Int32  | Номер строки, которую необходимо удалить. Нумерация начинается с единицы | `1`|
| Страница        | String | Наименование страницы Excel                                 | `"Лист1"` |
| Индекс страницы | Int32  | Порядковый номер страницы. Нумерация начинается с нуля. Если указано название страницы, номер можно пропустить | `0` |
 
## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

:small_orange_diamond: **Внимание**. До версии 1.24.2 метод `DeleteRows` удалял столбцы вместо строк. В версии 1.24.2 ошибка была исправлена, метод удаляет строки.

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//rowIdx - Индекс строки: [Int32] Индекс строки
//count - Количество: [Int32] Количество строк для удаления
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\rows.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
Int32 rowIdx=3;
Int32 count = 1;
app.DeleteRows(rowIdx,count,"Лист2",1);
app.Save();
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Кол-во: [Int32] Кол-во удаляемых строк
#index - Индекс: [Int32] Индекс строки, которую необходимо удалить
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#app.DeleteRows(index, range, [sheet], [sheetIdx])

app = LTools.Office.ExcelApp.Init(wf, ".\\rows.xlsx",";", LTools.Office.Model.InteropTypes.DX)
app.DeleteRows(3, 1, "Лист2", 1)
app.SaveAs(".\\rows.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Кол-во: [Int32] Кол-во удаляемых строк
//index - Индекс: [Int32] Индекс строки, которую необходимо удалить
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//app.DeleteRows(index, range, [sheet], [sheetIdx]); 
		
var app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\rows.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.DeleteRows(3, 1, "Лист2", 1);
app.SaveAs(".\\rows.xlsx");
```
{% endtab %}
{% endtabs %}
