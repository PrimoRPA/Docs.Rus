# Вставка диаграммы

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (177).png>)

![](<../../../.gitbook/assets/excel-create-chart.png>)

Элемент создает диаграмму на листе Excel. 

**Общие рекомендации**:

1. Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, то после вставки диаграммы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность его заполнения.

| Свойство             | Тип                   | Описание                         |
| -------------------- | --------------------- | -------------------------------- |
| ***Excel:***  | |  |
| Диапазон             | String   | Диапазон данных. Пример: `"A1:D12"`. Если не указан, будет использован выделенный диапазон. Если указан символ `"*"`, будет использован весь лист |
| Страница             | String   | Название страницы с указанной ячейкой. Пример: `"List1"` |
| Индекс страницы      | Int32    | Порядковый номер страницы, отсчет с 0. Пример: `0` |
| Высота               | Int32    | Высота диаграммы.  Пример: `800`  |
| Ширина               | Int32    | Ширина диаграммы.  Пример: `800`  |
| Сверху               | Int32    | Отступ сверху. Пример: `10` |
| Слева                | Int32    | Отступ слева. Пример: `10`      |
| Тип                  | -        | Тип диаграммы. По умолчанию **Area**. Чтобы изменить значение, щелкните выпадающий список |
| ***Вывод:***  | |  |
| Переменная\*         | LTools.Offile.Model.Excel.ExcelChartItem | Переменная, в которой будет храниться ссылка на диаграмму |

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):
  
{% tabs %}
{% tab title="C#" %}
```csharp
//LTools.Office.Model.Excel.ExcelChartItem data = app.InsertChart(range, cht, [sheet], [sheetIdx], [cLeft], [cTop], [cWidth], [cHeight]);

LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
LTools.Office.Model.Excel.ExcelChartItem data = app.InsertChart("*", LTools.Office.Model.Excel.ChartTypes.Line, "Лист1", 0, 10, 10, 800, 800);
app.SaveAs(".\\bookdiagram.xlsx");
```
{% endtab %}

{% tab title="Python" %}
```python
#data = app.InsertChart(range, cht, [sheet], [sheetIdx], [cLeft], [cTop], [cWidth], [cHeight]) #LTools.Office.Model.Excel.ExcelChartItem

app = LTools.Office.ExcelApp.Init(wf, ".\\book.xlsx", ";", LTools.Office.Model.InteropTypes.DX)
data = app.InsertChart("*", LTools.Office.Model.Excel.ChartTypes.Line, "Лист1", 0, 10, 10, 800, 800) #LTools.Office.Model.Excel.ExcelChartItem
app.SaveAs(".\\bookdiagram.xlsx")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, "c://Users//Alex//Documents//Primo//LearningPureCode//book.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);	
var data = app.InsertChart("*", _lib.LTools.Office.Model.Excel.ChartTypes.Line, "Лист1", 0, 10, 10, 800, 800) //_lib.LTools.Office.Model.Excel.ExcelChartItem
app.SaveAs("c://Users//Alex//Documents//Primo//LearningPureCode//bookdiagram.xlsx");
```
{% endtab %}
{% endtabs %}
