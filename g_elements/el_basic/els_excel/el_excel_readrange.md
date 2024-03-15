---
description: Read range
---

# Чтение диапазона

Элемент считывает данные из диапазона ячеек Excel и записывает их в переменную.

Путь до файла, тип драйвера и другие базовые настройки указываются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets/image (75).png>)

## Свойства
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство                | Тип                                              | Описание                                                          | Пример                |
| ----------------------- | ------------------------------------------------ | ----------------------------------------------------------------- | --------------------- |
| **Excel:**              |  |   |
| Диапазон                | String                                           | Диапазон считывания ячеек. Если вместо диапазона указать символ `"*"`, будет прочитан весь лист. <p>Если не указывать значение и использовать перед чтением элемент [Выделение диапазона](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_selectrange), то будет прочитан выделенный диапазон. </p>  <p>:small_blue_diamond: Диапазон указывается в соответствии с выбранным [стилем ссылок](https://learn.microsoft.com/ru-ru/office/troubleshoot/excel/numeric-columns-and-rows#more-information) заголовков строк и столбцов. По умолчанию задан стиль ссылок A1. Стиль выбирается в самом приложении Excel, а также в свойствах контейнера [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app) (см. состояние флага **R1C1**). </p>| `"A1:D12"` |
| Страница                | String                                           | Наименование страницы. Пример: `"List1"`                               |
| Индекс страницы         | Int32                                            | Индекс страницы - порядковый номер листа в книге Excel. Отсчет начинается с 0. Пример: `0` |
| Формат даты             | String                                           | Явное указание формата даты. Используется, когда нужно согласовать строковый вид даты с форматом поля DateTime. Пример: `"DD.MM.YYYY"` или `"MM/DD/YYYY"`|
| **Вывод:**             |  |   |              
| Строка заголовков       | Boolean                                          | Признак того, что первая строка содержит заголовки. При установке галочки - заголовки учитываются. Корректно работает только в переменной вывода DataTable. Учитывание заголовков впоследствии позволяет обращаться к данным столбца по его названию, а не индексу, что помогает снижать потенциальные ошибки |
| Учитывать типы полей ячеек Excel | Boolean                                 | Нужно ли учитывать типы ячеек в таблице Excel. При установке галочки типы будут учитываться |
| Переменная (текст)      | List\<List\<string>>                             | Переменная для хранения результатов чтения в виде текстовых значений |
| Переменная (информация) | List\<List \<[LTools.Office.Model.ExcelCellInfo](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/datatypes/excelcellinfo)>> | Переменная для хранения не только считанных данных, но и дополнительной информации о ячейках: например, о цвете шрифта |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-6.0) | Переменная для хранения результатов чтения в табличном виде |

:small_blue_diamond: **Примечание**. Выбор переменной вывода зависит от того, как дальше вы планируете обращаться к полученным данным. Например, выбрав переменную (таблица), затем можно обрабатывать считанные данные по колонкам. 

О том, как просмотреть при отладке процесса значение табличной переменной, можно узнать [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/debug#panel-vyvod). 



## Пример использования
RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **WorkWithExcelExamples**. Проект состоит из процессов-последовательностей.


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
