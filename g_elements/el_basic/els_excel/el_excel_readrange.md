# Чтение диапазона

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (10) (175).png>)

![](<../../../.gitbook/assets/image (75).png>)

Компонент считывает данные из диапазона ячеек Excel.

Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

## Свойства
Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство                | Тип                                              | Описание                                                          |
| ----------------------- | ------------------------------------------------ | ----------------------------------------------------------------- |
| ***Excel:***             |  |   |
| Диапазон                | String                                           | Диапазон считывания ячеек. Пример: `"A1:D12"`. Обратите внимание, что значение указывается в соответствии с выбранным [стилем ссылок](https://learn.microsoft.com/ru-ru/office/troubleshoot/excel/numeric-columns-and-rows#more-information) в приложении Excel и в свойствах контейнера [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app) (см. состояние флага **R1C1**). По умолчанию задан стиль ссылок A1. <p></p> <p>Если указать символ `"*"`, будет прочитан весь лист.</p> <p>Если не указывать значение и использовать перед чтением элемент [Выделение диапазона](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_selectrange), то будет прочитан выделенный диапазон</p>|
| Страница                | String                                           | Наименование страницы. Пример: `"List1"`                               |
| Индекс страницы         | Int32                                            | Индекс страницы - порядковый номер листа в книге Excel. Отсчет начинается с 0. Пример: `0` |
| Формат даты             | String                                           | Явное указание формата даты. Используется, когда нужно согласовать строковый вид даты с форматом поля DateTime. Пример: `"DD.MM.YYYY"` или `"MM/DD/YYYY"`|
| ***Вывод:***             |  |   |              
| Строка заголовков       | Boolean                                          | Признак того, что первая строка содержит заголовки. При установке галочки - заголовки учитываются. Корректно работает только в переменной вывода DataTable. Учитывание заголовков впоследствии позволяет обращаться к данным столбца по его названию, а не индексу, что помогает снижать потенциальные ошибки |
| Учитывать типы полей ячеек Excel | Boolean                                 | Нужно ли учитывать типы ячеек в таблице Excel. При установке галочки типы будут учитываться |
| Переменная (текст)      | List\<List\<string>>                             | Переменная для хранения результатов чтения в виде текстовых значений |
| Переменная (информация) | List\<List \<[LTools.Office.Model.ExcelCellInfo](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/datatypes/excelcellinfo)>> | Переменная для хранения не только считанных данных, но и дополнительной информации о ячейках: например, о цвете шрифта |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-6.0) | Переменная для хранения результатов чтения в табличном виде |

:small_blue_diamond: **Примечание**. Выбор переменной вывода зависит от того, как дальше вы планируете обращаться к полученным данным. Например, выбрав переменную (таблица), затем можно обрабатывать считанные данные по колонкам. 

О том, как просмотреть при отладке процесса значение табличной переменной, можно узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#panel-vyvod). 


## Обучающий пример

На портале Learning представлен обучающий RPA-проект [WorkWithExcelExample](https://github.com/PrimoRPA/Learning/tree/master/WorkWithExcelExample), в котором используются различные элементы Excel. **Чтение диапазона** находится в процессе под номером 4.1. 

Вы можете скачать и запустить обучающий проект, чтобы посмотреть результат чтения в переменной с типом DataTable, а также пример обработки этого результата.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
List<List<string>> data = app.ReadRange("A1:C12", "Лист1");
List<List<LTools.Office.Model.ExcelCellInfo>> data = app.ReadRangeInfo("A1:C12", "Лист1");
System.Data.DataTable data = app.ReadRangeTable("A1:C12", "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
data = app.ReadRange("A1:C12", "Лист1")
data = app.ReadRangeInfo("A1:C12", "Лист1")
data = app.ReadRangeTable("A1:C12", "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var data = app.ReadRange("A1:C12", "Лист1");
var data = app.ReadRangeInfo("A1:C12", "Лист1");
var data = app.ReadRangeTable("A1:C12", "Лист1");
```
{% endtab %}
{% endtabs %}
