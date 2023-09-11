# Запись диапазона

![](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (1) (59).png>)

![](<../../../.gitbook/assets/image (317).png>)

Элемент записывает данные в указанный диапазон ячеек Excel.

**Общие сведения**:

1. Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).
2. Если в файле требуется сохранить изменения, то после записи данных используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство                | Тип                                                                                                      | Описание                                                                                   |
| ----------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| _**Excel:**_             |                                                                                                          |                                                                                                                     |
| Диапазон\*              | String                                                                                                   | Диапазон записи ячеек. Пример: `"A1:D12"`                                                                            |
| Всю строку              | Boolean                                                                                                  | Добавить строку целиком. Свойство следует применять, если на странице Excel настроен фильтр                          |
| Добавлять заголовки     | Boolean                                                                                                  | Добавлять заголовки колонок таблицы                                                                                  |
| Страница                | String                                                                                                   | Наименование страницы                                                                                                |
| Индекс страницы         | Int32                                                                                                    | Порядковый номер страницы. Отсчет начинается с 0                                                                     |
| Как текст               | Boolean                                                                                                  | Установите галочку, чтобы вставить значение как текст. **Если установлена, то свойство «Строгая типизация» нужно выключить!** |
| Перезаписать            | Boolean                                                                                                  | Определите, нужно ли перезаписывать данные                                                                           |
| Направление             |                                                                                                          | Направление сдвига ячеек                                                                                              |
| Раширять диапазон       |                                                                                                          | Автоматически расширять диапазон до размеров данных                                                                   |
| Числовой формат         | String                                                                                                   | Формат вводимого числа (#,#)                                                                                          |
| Строгая типизация       | Boolean                                                                                                  | Признак строгой типизации таблиц (работает с обоими типами драйверов). По умолчанию включено. Строгая типизация не дает изменять формат данных при записи в таблицу. При отключении параметра возможна ситуация, когда числовой формат ошибочно преобразуетсся в строку |
| Переменная (текст)      | List\<List\<string>>                                                                                     | Переменная для хранения данных записи текстовых значений                                                            |
| Переменная (информация) | List\<List<[LTools.Office.Model.ExcelCellInfo](datatypes/excelcellinfo.md)>>                             | Переменная для хранения данных записи, содержащих информацию о ячейках                                              |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-7.0) | Переменная для хранения данных записи табличных значений                                                            |

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.AppendRange(new List<List<string>>(), "A1:B2", true, "Лист1", 0);
app.AppendRange(new List<List<LTools.Office.Model.ExcelCellInfo>>(), "A1:B2", true, null, 0);
app.AppendRange(new System.Data.DataTable(), "A1:B2", true, "Лист1");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
dt = List[List[String]]()
dt2 = List[List[LTools.Office.Model.ExcelCellInfo]]()
app.AppendRange(dt, "A1:B2", true, "Лист1", 0)
app.AppendRange(dt2, "A1:B2", true, null, 0)
app.AppendRange(System.Data.DataTable(), "A1:B2", true, "Лист1")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var lst = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.System.String)));
var lst2 = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Collections.Generic.List(_lib.LTools.Office.Model.ExcelCellInfo)));
var lst3 = host.newObj(_lib.System.Data.DataTable);
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.AppendRange(lst, "A1:B2", true, "Лист1", 0);
app.AppendRange(lst2, "A1:B2", true, null, 0);
app.AppendRange(lst3, "A1:B2", true, "Лист1");
```
{% endtab %}
{% endtabs %}
