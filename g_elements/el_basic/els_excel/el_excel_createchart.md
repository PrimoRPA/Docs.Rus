---
description: Insert chart
---


# Вставка диаграммы

Элемент создает диаграмму на листе Excel. 

Путь до файла, тип драйвера и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). Если в файле требуется сохранить изменения, то после вставки диаграммы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

![](<../../../.gitbook/assets1/WFCreateChart.png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность его заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство             | Тип                   | Описание                         | Пример             |
| -------------------- | --------------------- | -------------------------------- | ------------------ |
| **Excel:**  | |  |
| Диапазон             | String   | Диапазон данных. Если не указан, будет использован выделенный диапазон. Если указан символ `"*"`, будет использован весь лист | `"A1:D12"` |
| Страница             | String   | Название страницы в книге Excel         | `"List1"`  |
| Индекс страницы      | Int32    | Порядковый номер страницы. Нумерация начинается с нуля. Если указано название страницы, номер можно пропустить | `0`  |
| Высота               | Int32    | Высота диаграммы | `800`  |
| Ширина               | Int32    | Ширина диаграммы | `800`  |
| Сверху               | Int32    | Отступ сверху    | `0`    |
| Слева                | Int32    | Отступ слева     | `100`  |
| Тип                  | -        | Тип диаграммы. По умолчанию **Area** — диаграмма с областями. Чтобы изменить значение, щелкните выпадающий список | `Area` |
| **Вывод:**  | |  |
| Переменная\*         | LTools.Offile.Model.Excel.ExcelChartItem | Переменная, в которой будет храниться ссылка на диаграмму |   |

Типы доступных диаграмм можно разделить на:
1. Area — диаграмма с областями.
2. Bar — линейчатая диаграмма. 
3. Column — гистограмма.
4. Doughnut — кольцевая диаграмма.
5. Line Chart — линейный график. 
6. Pie — круговая диаграмма. 
7. XY scatter — точечная диаграмма.

Подробнее о видах диаграмм читайте здесь:
* [на русском языке](https://support.microsoft.com/ru-ru/office/%D1%82%D0%B8%D0%BF%D1%8B-%D0%B4%D0%B8%D0%B0%D0%B3%D1%80%D0%B0%D0%BC%D0%BC-%D0%B2-office-a6187218-807e-4103-9e0a-27cdb19afb90);
* [на английском](https://support.microsoft.com/en-us/office/available-chart-types-in-office-a6187218-807e-4103-9e0a-27cdb19afb90).

Пример заполненных свойств приведен на рисунке ниже. В данном случае диаграмму вставили по диапазону данных "А2:В12" листа "Копия персонала".

![](<../../../.gitbook/assets1/WFCreateChart-example.png>)


## Пример использования 
RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **WorkWithExcelExample**.
3. Элемент **Вставка диаграммы** находится в процессе `Main.ltw`. Описание процесса можно найти в файлах проекта. 


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Диапазон: [String] Диапазон данных (A1:D12). Если не указан, будет использован выделенный диапазон.  Если указан символ "*", будет использован весь лист
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//cht - Тип: Тип диаграммы
//cLeft - Слева: [Int32] Отступ слева
//cTop - Сверху: [Int32] Отступ сверху
//cWidth - Ширина: [Int32] Ширина диаграммы
//cHeight - Высота: [Int32] Высота диаграммы
//LTools.Office.Model.Excel.ExcelChartItem data = app.InsertChart(range, cht, [sheet], [sheetIdx], [cLeft], [cTop], [cWidth], [cHeight]);

LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
LTools.Office.Model.Excel.ExcelChartItem data = app.InsertChart("*", LTools.Office.Model.Excel.ChartTypes.Line, "Лист1", 0, 10, 10, 800, 800);
app.SaveAs(".\\bookdiagram.xlsx");
```
{% endtab %}

{% tab title="Python" %}
```python
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Диапазон: [String] Диапазон данных (A1:D12). Если не указан, будет использован выделенный диапазон.  Если указан символ "*", будет использован весь лист
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы
#cht - Тип: Тип диаграммы
#cLeft - Слева: [Int32] Отступ слева
#cTop - Сверху: [Int32] Отступ сверху
#cWidth - Ширина: [Int32] Ширина диаграммы
#cHeight - Высота: [Int32] Высота диаграммы
#data = app.InsertChart(range, cht, [sheet], [sheetIdx], [cLeft], [cTop], [cWidth], [cHeight]) #LTools.Office.Model.Excel.ExcelChartItem

app = LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
data = app.InsertChart("*", LTools.Office.Model.Excel.ChartTypes.Line, "Лист1", 0, 10, 10, 800, 800) #LTools.Office.Model.Excel.ExcelChartItem
app.SaveAs(".\\bookdiagram.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Диапазон: [String] Диапазон данных (A1:D12). Если не указан, будет использован выделенный диапазон.  Если указан символ "*", будет использован весь лист
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы
//cht - Тип: Тип диаграммы
//cLeft - Слева: [Int32] Отступ слева
//cTop - Сверху: [Int32] Отступ сверху
//cWidth - Ширина: [Int32] Ширина диаграммы
//cHeight - Высота: [Int32] Высота диаграммы

var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);	
var data = app.InsertChart("*", _lib.LTools.Office.Model.Excel.ChartTypes.Line, "Лист1", 0, 10, 10, 800, 800) //_lib.LTools.Office.Model.Excel.ExcelChartItem
app.SaveAs(".\\book.xlsx");
```
{% endtab %}
{% endtabs %}
