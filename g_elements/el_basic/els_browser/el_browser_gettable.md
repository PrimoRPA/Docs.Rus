# Прочитать таблицу 
_Eng: Read Table_



![Read Table 2](<../../../.gitbook/assets/image (207).png>)

Этот элемент предназначен для чтения данных из табличного элемента управления. Он корректно работает только внутри контейнера "Открыть браузер" или "Присоединиться к браузеру".

Кнопка "Мастер" запускает процесс чтения таблицы. После нажатия этой кнопки появляется окно приветствия.

![Welcome Window](<../../../.gitbook/assets/image (87).png>)

После этого необходимо выбрать в браузере элемент, который вы хотите считать строкой таблицы.

![Capture Element](<../../../.gitbook/assets/image (237).png>)

Затем появляется стандартное окно для формирования шаблона поиска.

![Search Template](<../../../.gitbook/assets/image (129).png>)

После завершения этого процесса появляется окно для формирования ячеек строки.

![Cell Configuration](<../../../.gitbook/assets/image (225).png>)

В этом окне необходимо отметить галочками группы данных и атрибуты, которые вы хотите считывать в качестве ячеек. Вы также можете указать имена для колонок таблицы (в колонке "Имя колонки"). Также есть возможность скорректировать CSS-селекторы данных или создать новые CSS-селекторы. После завершения этого процесса, можно нажать кнопку "Проверить", после чего появится окно с результатами.

![Resulting Data](<../../../.gitbook/assets/image (144).png>)

Свойства этой активности:

- **Шаблон поиска**: Строка. Это шаблон для поиска элемента управления.
- **Элемент**: Ссылка на элемент управления.
- **Тэг строки\***: Строка. Тэг элемента строки.
- **Тэг колонки\***: Строка. Тэг элемента колонки.
- **Тэг заголовка**: Строка. Тэг элемента заголовка.
- **Переменная**: Переменная для хранения результатов чтения таблицы.
- **Переменная (таблица)**: Переменная для хранения результатов чтения таблицы в формате System.Data.DataTable.
- **Мастер**: Строка. Шаблон, полученный через Мастер.
- **Таймаут\***: Целое число. Предельное время ожидания завершения процесса (в миллисекундах).

Пример проекта можно загрузить по ссылке: https://github.com/PrimoRPA/Learning/blob/master/StudioActivities/Ru/%D0%91%D1%80%D0%B0%D1%83%D0%B7%D0%B5%D1%80/%D0%9F%D1%80%D0%BE%D1%87%D0%B8%D1%82%D0%B0%D1%82%D1%8C%20%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D1%83.ltw

Примеры кода для разных языков:

### C#

```csharp
LTools.WebBrowser.BrowserApp app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
LTools.WebBrowser.Model.WebDataTable tbl = app.ReadDataGrid("{\"Tag\":\"DIV\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"header-bar\"}]}", "A", "SPAN");
//Элемент
LTools.WebBrowser.Model.IElementInfo el = app.FindElement("{\"Tag\":\"DIV\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"header-bar\"}]}");
tbl = app.ReadDataGrid(el, "A", "SPAN");		
foreach (var r in tbl.Data)
	foreach (var c in r)
		LTools.Workflow.PrimoApp.AddToLog(wf, c);	
```

### Python

```python
app = LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", LTools.WebBrowser.Model.BrowserTypes_Short.IE)
#Шаблон поиска
tbl = app.ReadDataGrid("{\"Tag\":\"DIV\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"header-bar\"}]}", "A", "SPAN")
#Элемент
el = app.FindElement("{\"Tag\":\"DIV\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"header-bar\"}]}")
tbl = app.ReadDataGrid(el, "A", "SPAN")
for r in tbl.Data:
	for c in r:
		LTools.Workflow.PrimoApp.AddToLog(wf, c)
```

### JavaScript

```javascript
var app = _lib.LTools.WebBrowser.BrowserApp.Init(wf, "Free email*", _lib.LTools.WebBrowser.Model.BrowserTypes_Short.IE);
//Шаблон поиска
var tbl = app.ReadDataGrid("{\"Tag\":\"DIV\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"header-bar\"}]}", "A", "SPAN");
//Элемент
var el = app.FindElement("{\"Tag\":\"DIV\",\"SearchFrames\":false,\"Attributes\":[{\"Key\":\"CLASS\",\"Value\":\"header-bar\"}]}");
tbl = app.ReadDataGrid(el, "A", "SPAN");	
for (var i = 0; i < tbl.Data.Count; i++)
	for (var j = 0; j < tbl.Data[i].Count; j++)
		_lib.LTools.Workflow.PrimoApp.AddToLog(wf, tbl.Data[i][j]);
```
