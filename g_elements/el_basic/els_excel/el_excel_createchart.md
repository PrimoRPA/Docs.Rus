# Вставка диаграммы

![](<../../../.gitbook/assets/excel-create-chart.png>)

Элемент создает диаграмму на листе Excel. 

**Общие сведения**:

1. Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, то после вставки диаграммы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

### Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                         |
| -------------------- | --------------------- | -------------------------------- |
| **Excel:**  | |  |
| Диапазон             | String   | Диапазон данных. Пример: `"A1:D12"`. Если не указан, будет использован выделенный диапазон. Если указан символ `"*"`, будет использован весь лист |
| Страница             | String   | Название страницы с указанной ячейкой. Пример: `"List1"` |
| Индекс страницы      | Int32    | Порядковый номер страницы, отсчет с 0. Пример: `0` |
| Высота               | Int32    | Высота диаграммы.  Пример: `800`  |
| Ширина               | Int32    | Ширина диаграммы.  Пример: `800`  |
| Сверху               | Int32    | Отступ сверху. Пример: `0` |
| Слева                | Int32    | Отступ слева. Пример: `100`      |
| Тип                  | -        | Тип диаграммы. По умолчанию **Area** - диаграмма с областями. Чтобы изменить значение, щелкните выпадающий список |
| ***Вывод:***  | |  |
| Переменная\*         | LTools.Offile.Model.Excel.ExcelChartItem | Переменная, в которой будет храниться ссылка на диаграмму |

Типы доступных диаграмм можно разделить на:
1. Area - диаграмма с областями.
2. Bar - линейчатая диаграмма. 
3. Column - гистограмма.
4. Doughnut - кольцевая диаграмма.
5. Line Chart - линейный график. 
6. Pie - круговая диаграмма. 
7. XY scatter - точечная диаграмма.

Подробнее о видах диаграмм читайте здесь:
* [на русском языке](https://support.microsoft.com/ru-ru/office/%D1%82%D0%B8%D0%BF%D1%8B-%D0%B4%D0%B8%D0%B0%D0%B3%D1%80%D0%B0%D0%BC%D0%BC-%D0%B2-office-a6187218-807e-4103-9e0a-27cdb19afb90);
* [на английском](https://support.microsoft.com/en-us/office/available-chart-types-in-office-a6187218-807e-4103-9e0a-27cdb19afb90).

### Обучающий пример 
Проект, в котором демонстрируется вставка диаграммы, можно найти [здесь](https://github.com/PrimoRPA/Learning/tree/master/WorkWithExcelExample). Он имеет название WorkWithExcelExample, в качестве типа процесса выбрана **Последовательность**. Чтобы просмотреть проект, скачайте и загрузите его в Студию. Элемент **Вставка диаграммы** идет в процессе под номером 3.18. Описание процесса находится в файлах проекта.

### Только код
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
