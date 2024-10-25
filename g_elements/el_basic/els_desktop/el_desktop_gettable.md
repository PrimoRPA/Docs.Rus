# Чтение таблицы

*Eng: Read table*

![](<../../../.gitbook/assets/image (93).png>)

Элемент предназначен для автоматического извлечения данных из табличных элементов в пользовательских интерфейсах. Он корректно работает только внутри контейнера **Присоединиться к приложению**. Компонент считывает данные из таблицы, разделяет их на строки и столбцы, и сохраняет результаты в переменные для дальнейшего использования. 


### Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. 

| Свойство             | Тип                                                          | Описание                                           |
| -------------------- | ------------------------------------------------------------ | -------------------------------------------------- |Выв
|**Вывод** | |
| Переменная           | [LTools.Desktop.Model.UIDataTable](datatypes/uidatatable.md) | Переменная для хранения результатов чтения таблицы |
| Переменная (таблица) | System.Data.DataTable                                        | Переменная для хранения результатов чтения таблицы |
|**Общие** | |
| Наименование         | String                                                       | Название операции чтения таблицы                   |
| Отключить логирование | Boolean                                                     | Отключение логирования данной операции              |
| Пауза до (мс)        | Int32                                                        | Время ожидания перед началом операции (мс)          |
| Пауза после (мс)     | Int32                                                        | Время ожидания после завершения операции (мс)       |
| Продолжить при ошибке | Boolean                                                     | Продолжение выполнения сценария в случае ошибки    |
| Скриншот завершения  | Boolean                                                      | Сделать скриншот после завершения операции          |
| Скриншот ошибки      | Boolean                                                      | Сделать скриншот в случае ошибки                    |
| **Процесс** |  |
| Алгоритм             | String                                                       | Определяет способ чтения таблицы (Actual, Table Move) |
| Количество колонок   | Int32                                                        | Количество столбцов таблицы для более точного чтения и разделения данных. **Функция доступна с версии Студии 1.24.8**|
| Область              | String                                                      | Координаты области, в которой происходит чтение данных |
| Обнаружить заголовки | Boolean                                                      | Формирует заголовки из повторяющихся данных. Если все ячейки столбца содержат одинаковые значения, это значение объединяется с названием столбца в единый заголовок. **Функция доступна с версии Студии 1.24.8** |
| Таймаут\*            | Int32                                                        | Предельное время ожидания завершения процесса (мс) |
| Шаблон поиска        | String                                                       | Шаблон поиска элемента управления                  |
| Элемент              | LTools.Desktop.Model.DUIControl                              | Ссылка на элемент управления                       |

*Алгоритм:* Определяет способ чтения таблицы.
- *Actual:* Работает в зависимости от условий, обеспечивает чтение данных.
- *Table Move:* Новый алгоритм (доступен только для Win32), предназначенный для полного считывания данных из виртуальных таблиц. *Функция доступна с версии 1.24.8*

### Свойства LTools.Desktop.Model.UIDataTable

- **RowCount**: `[Int32]` Количество строк
- **ColumnCount**: `[Int32]` Количество столбцов
- **Headers**: `[List<String>]` Заголовки колонок
- **Data**: `[List<List<String>>]` Данные таблицы


![Новый алгоритм Table Move](<../../../.gitbook/assets1/tablemove.png>)


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code)

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Desktop.DesktopApp app = LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
LTools.Desktop.Model.UIDataTable tbl = app.ReadDataGrid("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
//Элемент
LTools.Desktop.Model.DUIControl el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
tbl = app.ReadDataGrid(el);
foreach (var r in tbl.Data)
	foreach (var c in r)
		LTools.Workflow.PrimoApp.AddToLog(wf, c);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Desktop.DesktopApp.Init(wf, None, "Test_*", 20000, True, LTools.Desktop.Model.DesktopTypes.UIAUTOMATION)
#Шаблон поиска
tbl = app.ReadDataGrid("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
#Элемент
el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}")
tbl = app.ReadDataGrid(el)
for r in tbl.Data:
	for c in r:
		LTools.Workflow.PrimoApp.AddToLog(wf, c)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Desktop.DesktopApp.Init(wf, null, "Test_*", 20000, true, _lib.LTools.Desktop.Model.DesktopTypes.UIAUTOMATION);
//Шаблон поиска
var tbl = app.ReadDataGrid("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
//Элемент
var el = app.FindElement("{\"Name\":\"\",\"AutomationID\":\"dtgrdSample\",\"ClassName\":\"DataGrid\",\"AUIProperties\":[],\"TextSearchMode\":0,\"IsRoot\":false,\"IsQuickSearch\":false}");
tbl = app.ReadDataGrid(el);
for (var i = 0; i < tbl.Data.Count; i++)
	for (var j = 0; j < tbl.Data[i].Count; j++)
		_lib.LTools.Workflow.PrimoApp.AddToLog(wf, tbl.Data[i][j]);
```
{% endtab %}
{% endtabs %}

