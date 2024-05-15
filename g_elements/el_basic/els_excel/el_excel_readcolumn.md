---
description: Read column
---


# Чтение колонки

Элемент считывает данные из указанного столбца и сохраняет результат в переменную. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets1/WFReadColumn.png>)



## Свойства
Символ `*` в названии свойства указывает на обязательность его заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство             | Тип                   | Описание                         | Пример       |
| -------------------- | --------------------- | -------------------------------- | ------------ |
| **Excel:**  | | |
| Ячейка\*             | String   | Идентификатор начальной ячейки                | `"B2"`       |
| Страница             | String   | Название страницы с указанным столбцом      | `"Лист1"`    |
| Индекс страницы      | Int32    | Порядковый номер страницы, начинается с нуля         | `0`          |
| **Вывод:**  | | |
| Данные\*             | List\<Object\> | Название переменной для записи данных из колонки |     |

**Пример заполненных свойств**:

![](<../../../.gitbook/assets/excel-read-column2.png>)


## Пример использования
RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **WorkWithExcelExamples**. Проект состоит из процессов-последовательностей.


## Только код
Ниже приведен пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell- Ячейка: [String] Идентификатор ячейки (A1), с которой начинается чтение
//data - Данные: [List<Object>] Данные в формате списка объектов
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
String cell="A2";
List<Object> data = app.ReadColumn(cell,"Лист1",0);
		
foreach (object value in data)
{
    LTools.Workflow.PrimoApp.AddToLog(wf, value.ToString(), LTools.Enums.LogMessageType.Info);
}
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#cell - Ячейка: [String] Идентификатор начальной ячейки (A4)
#data - Данные: [List<Object>] Данные, полученные из колонки
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
		
app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
cell = "A2"
data = app.ReadColumn(cell, "Лист1", 0) #List<Object>
       
#Вывод в лог
for value in data:
    LTools.Workflow.PrimoApp.AddToLog(wf, str(value), LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//cell - Ячейка: [String] Идентификатор начальной ячейки (A4)
//data - Данные: [List<Object>] Данные, полученные из колонки
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы

let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var cell = "A2";
var data = app.ReadColumn(cell, "Лист1", 0); //List<Object>
		
//Вывод в лог	
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, data[0].toString(), _lib.LTools.Enums.LogMessageType.Info);
		
//Вывод в лог	
for(var index = 0; index < data.length; ++index){
    _lib.LTools.Workflow.PrimoApp.AddToLog(wf, data[index].toString(), _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}
