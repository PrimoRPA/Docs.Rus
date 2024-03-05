---
description: Append range
---

# Запись диапазона

Элемент записывает данные в диапазон ячеек. Диапазон указывается в свойствах элемента.

Путь до файла, тип драйвера и прочие параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets/image (317).png>)

:small_orange_diamond: ***Чтобы сохранить новые данные в файле, используйте в конце работы элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save).***


## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство                | Тип                                                                                                      | Описание                                                                                   |
| ----------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ |
| _**Excel:**_             |                                                                                                         |                                                                                                                     |
| Диапазон\*              | String                                                                                                   | Диапазон ячеек для записи данных. Пример: `"A1:D12"`                                                                            |
| Всю строку              | Boolean                                                                                                  | Определяет, нужно ли добавлять строку целиком. По умолчанию отлючено. Свойство следует применять, если на странице Excel настроен фильтр  |
| Добавлять заголовки     | Boolean                                                                                                  | Определяет, нужно ли добавлять заголовки колонок. По умолчанию отлючено - заголовки не записываются в таблицу           |
| Страница                | String                                                                                                   | Наименование страницы. Пример: `"List1"`                                                                    |
| Индекс страницы         | Int32                                                                                                    | Порядковый номер страницы. Пример: `0`                                                                              |
| Строгая типизация       | Boolean                                                                                                  | Признак строгой типизации таблиц (работает с обоими драйверами). По умолчанию строгая типизация включена - это не дает изменить формат данных при записи в таблицу. Если параметр отключить, то возможна ситуация, когда числовой формат ошибочно преобразуется в строку |
| Как текст               | Boolean                                                                                                  | Определяет, нужно ли вставить значение как текст. По умолчанию отключено. <p>**Если галочка установлена, то свойство «Строгая типизация» нужно выключить** </p>|
| Перезаписать            | Boolean                                                                                                  | Определяет, нужно ли перезаписывать данные. По умолчанию свойство отключено - перезапись не разрешается               |
| Направление             |                                                                                                          | Направление сдвига ячеек. Возможные значения: 1) Down - по умолчанию; 2) Right                                        |
| Расширять диапазон      | Boolean                                                                                                  | Определяет, нужно ли автоматически расширять диапазон до размеров данных. По умолчанию отключено - диапазон не расширяется |
| Числовой формат         | String                                                                                                   | Формат вводимого числа (#,#)                                                                                          |
| Переменная (текст)      | List\<List\<string>>                                                                                     | Переменная для хранения данных записи текстовых значений                                                            |
| Переменная (информация) | List\<List<[LTools.Office.Model.ExcelCellInfo](datatypes/excelcellinfo.md)>>                             | Переменная для хранения данных записи, содержащих информацию о ячейках                                              |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-7.0) | Переменная для хранения данных записи табличных значений                                                            |

## Пример использования



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
