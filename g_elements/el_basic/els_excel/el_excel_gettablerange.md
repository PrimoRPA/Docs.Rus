---
description: Get table range
---

# Получение диапазона таблицы

Элемент помогает вычислить диапазон таблицы по ее названию. Под таблицей в Excel подразумевается диапазон ячеек, отформатированый в виде таблицы для того, чтобы легче было управлять группой связанных данных. Подробнее о понятии **Таблица** читайте [здесь](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D1%89%D0%B8%D0%B5-%D1%81%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BE-%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%D1%85-excel-7ab0bb7d-3a9e-4b56-a3c9-6c94334e492c).

Путь до файла и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets1/WFGetTableRange.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание               | Пример       |
| --------------- | ------ | ---------------------- | ------------ |
| **Excel:**      |        |                        |              |
| Таблица\*       | String | Название таблицы       | `"TableExample"` |
| Страница        | String | Название страницы в книге Excel | `"Лист1"` |
| Индекс страницы | Int32  | Номер страницы в книге Excel. Нумерация начинается с нуля | `0` |
| **Вывод:**      |        |                        |              |
| Диапазон\*      | String | Название переменной, в которую запишется найденный диапазон таблицы |  |

## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//name - Таблица: [String] Наименование таблицы
//data - Диапазон: [String] Диапазон таблицы
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
string data = app.GetTableRange("TableExample", "Лист1", 0);

//Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, data, LTools.Enums.LogMessageType.Info);
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#name - Таблица: [String] Наименование таблицы
#data - Диапазон: [String] Диапазон таблицы
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы

app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx",";", LTools.Office.Model.InteropTypes.DX)
data = app.GetTableRange("TableExample", "Лист1", 0) #String

#Вывод в лог
LTools.Workflow.PrimoApp.AddToLog(wf, data, LTools.Enums.LogMessageType.Info)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//name - Таблица: [String] Наименование таблицы
//data - Диапазон: [String] Диапазон таблицы
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы

let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var data = app.GetTableRange("TableExample", "Лист1", 0); //String

//Вывод в лог
_lib.LTools.Workflow.PrimoApp.AddToLog(wf, data, _lib.LTools.Enums.LogMessageType.Info);
```
{% endtab %}
{% endtabs %}

