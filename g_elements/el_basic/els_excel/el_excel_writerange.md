---
description: Append range
---

# Запись диапазона

Элемент записывает данные в диапазон ячеек Excel. Данные указываются в виде переменной. Переменная может содержать текстовое значение, таблицу либо информацию о ячейках — тип данных переменной следует выбирать на свое усмотрение в свойствах элемента.

Путь до файла задается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). В конце работы c файлом используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save), чтобы изменения применились.

![](<../../../.gitbook/assets1/append-range-with-save.png>)



## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


| Свойство                | Тип                                                                                                      | Описание                                                                                   | Пример       |
| ----------------------- | -------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------ | ------------ |
| **Excel:**       | |   |    |
| Диапазон\*              | String                                                                                                   | Диапазон ячеек для записи данных                                                           | `"A1:D12"`   |
| Страница                | String                                                                                                   | Наименование страницы Excel. Если указан индекс страницы, то название можно не заполнять | `"List1"`    |
| Индекс страницы         | Int32                                                                                                    | Порядковый номер страницы, начинается с нуля. Если указан номер страницы вместо названия, то в файле допускается переименовывать страницы | `0`          |
| Создавать лист          | Boolean                                                                                                  | Определяет, нужно ли создавать лист в случае, если его не существует. По умолчанию отключено — лист не создается |  |
| Всю строку              | Boolean                                                                                                  | Определяет, нужно ли добавлять строку целиком. По умолчанию отключено. Свойство рекомендуется применять, если на странице Excel настроен фильтр  |  |
| Добавлять заголовки     | Boolean                                                                                                  | Определяет, нужно ли добавлять заголовки колонок. По умолчанию отлючено — заголовки не записываются в таблицу   |  |
| Строгая типизация       | Boolean                                                                                                  | Признак строгой типизации таблиц. По умолчанию строгая типизация включена — это не дает изменить формат данных при записи в таблицу. Если параметр отключить, то возможна ситуация, когда числовой формат ошибочно преобразуется в строку | |
| Как текст               | Boolean                                                                                                  | Определяет, нужно ли вставлять значение как текст. По умолчанию отключено. <p>:small_orange_diamond: **Если чекбокс установлен, то свойство «Строгая типизация» нужно выключить** </p>| |
| Перезаписать            | Boolean                                                                                                  | Определяет, нужно ли перезаписывать данные. По умолчанию свойство отключено — перезапись не разрешается | |
| Направление             |                                                                                                          | Направление сдвига ячеек. Возможные значения: 1) `Down` — по умолчанию; 2) `Right`             | `Down`    |
| Расширять диапазон      | Boolean                                                                                                  | Определяет, нужно ли автоматически расширять диапазон до размеров данных. По умолчанию отключено — диапазон не расширяется |  |
| Числовой формат         | String                                                                                                   | Формат вводимого числа                                                                         | `#,#`     |
| Переменная (таблица)    | [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-8.0&viewFallbackFrom=net-4.6.1) | Название переменной для записи табличных данных                     |  | 
| Переменная (текст)      | List\<List\<string>>                                                                                     | Название переменной для записи текстовых данных                                                |  |
| Переменная (информация) | List\<List<[LTools.Office.Model.ExcelCellInfo](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/datatypes/excelcellinfo)>>   | Название переменной для записи данных, содержащих информацию о ячейках |  |

## Пример использования

RPA-проект, демонстрирующий работу элемента, можно найти в нашем публичном репозитории [Learning](https://github.com/PrimoRPA/Learning).

1. Скачайте архив со всеми обучающими материалами по ссылке: [Скачать архив Learning](https://github.com/PrimoRPA/Learning/archive/refs/heads/master.zip).
2. Распакуйте архив и откройте в Студии проект **WorkWithExcelExamples**.


## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код (Pure code)**:

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
