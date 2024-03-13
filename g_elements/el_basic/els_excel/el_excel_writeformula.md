# Ввод формулы в ячейку

Элемент записывает формулу в ячейку Excel.

![](<../../../.gitbook/assets/Ввод формулы в ячейку. Excel.png>)

**Примечания**:

1. Путь до файла, тип драйвера и другие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, то после ввода формулы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип    | Описание                                                                                                  | Пример        |
| --------------- | ------ | --------------------------------------------------------------------------------------------------------- | ------------- |
| _**Excel:**_    |        |                                                                                                           |               |
| Ячейка\*        | String | Идентификатор ячейки для ввода формулы                                                                    | `"A3"`        |
| Формула\*       | String | Формула, которую нужно записать в ячейку. Оба драйвера (Interop и DX) поддерживают ввод формулы на русском и английском языках  | `"=СУММ(A1:A2)"`  |
| Страница        | String | Наименование страницы Excel, на которой находится ячейка                                                  | `"List 1"`    |
| Индекс страницы | Int32  | Порядковый номер страницы. Отсчет начинается с 0                                                          | `0`           |


## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор ячейки (A4)
//data - Формула: [String] Формула для записи в ячейку
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//String data = app.WriteCellFormula(cell, [data], [sheet], [sheetIdx]);
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\formula.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
String data="=SUM(C1:C10)";
app.WriteCellFormula("C11",data,"Лист2", 1);
app.Calculate();
app.SaveAs(".\\formula.xlsx");
```
{% endtab %}
