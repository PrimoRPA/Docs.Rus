---
description: Delete rows
---


# Удаление строк

![](<../../../.gitbook/assets/image (536).png>)

Элемент удаляет выбранные строки из листа Excel.

**Примечания**:

1. Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле нужно сохранить изменения, то после удаления строк используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип    | Описание                                                    | Пример    |
| --------------- | ------ | ----------------------------------------------------------- | --------- |
| Кол-во\*        | Int32  | Количество удаляемых строк                                  | `1`       |
| Индекс\*        | Int32  | Номер строки, которую необходимо удалить. Отсчет с 1        | `1`       |
| Страница        | String | Наименование страницы Excel                                 | `"Лист1"` |
| Индекс страницы | Int32  | Порядковый номер страницы, отсчет с 0                       | `0`       |
 
## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

:small_orange_diamond: **Внимание**. До версии 1.24.2 метод `DeleteRows` в C# удалял столбцы вместо строк. В версии 1.24.2 ошибка была исправлена, метод удаляет строки.

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//rowIdx - Индекс строки: [Int32] Индекс строки
//count - Количество: [Int32] Количество строк для удаления
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\columns-rows.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
Int32 rowIdx=3;
Int32 count = 2;
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

app = LTools.Office.ExcelApp.Init(wf, ".\\columns-rows.xlsx",";", LTools.Office.Model.InteropTypes.DX)
app.DeleteRows(3, 1, "Лист2", 1)
app.SaveAs(".\\columns-rows.xlsx")
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
		
let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\columns-rows.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.DeleteRows(2, 1, "Лист2", 1);
app.SaveAs(".\\columns-rows.xlsx");
```
{% endtab %}
{% endtabs %}
