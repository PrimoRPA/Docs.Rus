---
description: Delete columns
---

# Удаление колонок

![](<../../../.gitbook/assets/image (473).png>)

Элемент удаляет выбранные колонки из листа Excel.

**Примечания**:

1. Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, то после удаления колонок используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa). Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип    | Описание                                                     | Пример         |
| --------------- | ------ | ------------------------------------------------------------ | -------------- |
| Кол-во\*        | Int32  | Количество удаляемых колонок                                 | `1`            |
| Индекс\*        | Int32  | Порядковый номер колонки, которую необходимо удалить. Отсчет с 1 |  `1`       |
| Страница        | String | Наименование страницы Excel, на которой находится колонка    | `"Лист1"`      |
| Индекс страницы | Int32  | Порядковый номер страницы с колонкой. Отсчет с 0             | `0`            |

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

:small_orange_diamond: **Внимание**. До версии 1.24.2 метод `DeleteColumns` удалял строки вместо столбцов. В версии 1.24.2 ошибка была исправлена, метод удаляет столбцы.

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//columnIdx - Индекс колонки: [Int32] Индекс колонки
//count - Количество: [Int32] Количество колонок для удаления
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\columns.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
Int32 columnIdx=2;
Int32 count = 1;
app.DeleteColumns(columnIdx,count,"Лист2",1); 
app.Save();
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента: 
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Кол-во: [Int32] Кол-во удаляемых колонок
#index - Индекс: [Int32] Индекс колонки, которую необходимо удалить
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#app.DeleteColumns(index, range, [sheet], [sheetIdx])

app = LTools.Office.ExcelApp.Init(wf, ".\\columns.xlsx",";", LTools.Office.Model.InteropTypes.DX)
app.DeleteColumns(2, 1, "Лист2", 1)
app.SaveAs(".\\columns.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Кол-во: [Int32] Кол-во удаляемых колонок
//index - Индекс: [Int32] Индекс колонки, которую необходимо удалить
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//app.DeleteColumns(index, range, [sheet], [sheetIdx]);
		
var app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\columns.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.DeleteColumns(2, 1, "Лист2", 1);
app.SaveAs(".\\columns.xlsx");
```
{% endtab %}
{% endtabs %}
