# Прочитать таблицу 
_Eng: Read Table_

Элемент предназначен для чтения данных из табличного элемента управления. Для корректной работы следует помещать его в контейнер [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) или [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach).

По кнопке **Мастер** открывается мастер чтения таблиц. 

![Read Table 2](<../../../.gitbook/assets/image (207).png>)

Нажмите в окне мастера кнопку **Захват**.

![Welcome Window](<../../../.gitbook/assets/image (87).png>)

После чего выделите в браузере элемент, который следует считать строкой таблицы.

![Capture Element](<../../../.gitbook/assets/image (237).png>)

Появится стандартное окно для формирования шаблона поиска (селектора). Установите необходимые свойства для идентификации элемента управления и нажмите **ОК**.

![Search Template](<../../../.gitbook/assets/image (129).png>)

В результате отобразится окно для формирования ячеек строки. Отметьте галочками группы данных и атрибуты, которые вы хотите считывать в качестве ячеек. Вы также можете указать имена для колонок таблицы (в столбце **Имя колонки**) и скорректировать CSS-селекторы данных или создать новые CSS-селекторы. 

В завершение нажмите кнопку **Проверить**, чтобы просмотреть окно с результатами.

![Cell Configuration](<../../../.gitbook/assets/image (225).png>)

Пример результата:

![Resulting Data](<../../../.gitbook/assets/image (144).png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа «Процесс»**:

- **Тэг строки\***. String. Тег элемента строки.
- **Тэг колонки\***. String. Тег элемента колонки.
- **Тэг заголовка**. String. Тег элемента заголовка.
- **Мастер**. String. Шаблон для поиска элемента управления (то же, что и селектор), полученный через Мастер. 
- **Шаблон поиска**. String. Шаблон поиска элемента управления. 
- **Элемент**. LTools.WebBrowser.Model.IElementInfo. Переменная со ссылкой на элемент управления. Такую переменную можно получить при помощи компонента [**Присутствие элемента**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_exists), а потом указать ее в этом свойстве. Для этого откройте редактор кода и укажите `<название переменной>.BrowserElement`. Пример:

  ![](<../../../.gitbook/assets/execute-js-browser-element.png>)
  
- **Таймаут\***. Int32. Предельное время ожидания завершения процесса (в миллисекундах). По умолчанию `10000`.

**Группа «Вывод»**:

- **Переменная**. [LTools.WebBrowser.Model.WebDataTable](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/datatypes/webdatatable). Переменная для хранения результатов чтения таблицы.
- **Переменная (таблица)**. DataTable. Переменная для хранения результатов чтения таблицы в формате System.Data.DataTable.


## Пример на Learning 

Скачайте на [Learning](https://github.com/PrimoRPA/Learning) обучающий проект **StudioActivities**, чтобы просмотреть готовый RPA-процесс по работе с элементом **Прочитать таблицу**. Процесс находится по пути StudioActivities > Ru > Браузер > Прочитать таблицу.ltw. Откройте проект в Студии и запустите процесс.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

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
