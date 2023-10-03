# Прочитать таблицу

![](<../../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (266).png>)

![](<../../../../.gitbook/assets/image (207).png>)

Компонент, производящий чтение данных табличного элемента управления. Компонент корректно работает только внутри контейнера "Открыть браузер" либо "Присоединиться к браузеру".

Кнопка "Мастер" служит для запуска мастера чтения таблицы. При запуске мастера появляется окно приветствия

![](<../../../../.gitbook/assets/image (87).png>)

После нажатия кнопки "Захват", необходимо выбрать в браузере элемент, который будет считаться строкой таблицы

![](<../../../../.gitbook/assets/image (237).png>)

После выбора элемента появляется стандартное окно формирования шаблона поиска

![](<../../../../.gitbook/assets/image (129).png>)

Следом за ним появляется окно формирования ячеек строки

![](<../../../../.gitbook/assets/image (225).png>)

В данном окне необходимо галками выбрать группы данных и атрибуты, которые будут считываться в качестве ячеек. Также можно указать имена для колонок таблицы (в колонке "Имя колонки"). Также можно скорректировать CSS-селекторы данных, либо создать новые CSS-селекторы. По завершении, можно нажать кнопку "Проверить", после чего будет отображено окно результирующих данных

![](<../../../../.gitbook/assets/image (144).png>)

| Свойство             | Тип                                                               | Описание                                           |
| -------------------- | ----------------------------------------------------------------- | -------------------------------------------------- |
| Шаблон поиска        | String                                                            | Шаблон поиска элемента управления                  |
| Элемент              | LTools.WebBrowser.Model.IElementInfo                              | Ссылка на элемент управления                       |
| Тэг строки\*         | String                                                            | Тэг элемента строки                                |
| Тэг колонки\*        | String                                                            | Тэг элемента колонки                               |
| Тэг заголовка        | String                                                            | Тэг элемента заголовка                             |
| Переменная           | [LTools.WebBrowser.Model.WebDataTable](datatypes/webdatatable.md) | Переменная для хранения результатов чтения таблицы |
| Переменная (таблица) | System.Data.DataTable                                             | Переменная для хранения результатов чтения таблицы |
| Мастер               | String                                                            | Шаблон, полученный Мастером                        |
| Таймаут\*            | Int32                                                             | Предельное время ожидания завершения процесса (мс) |

{% tabs %}
{% tab title="C#" %}
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
{% endtab %}

{% tab title="Python" %}
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
{% endtab %}

{% tab title="JavaScript" %}
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
{% endtab %}
{% endtabs %}
