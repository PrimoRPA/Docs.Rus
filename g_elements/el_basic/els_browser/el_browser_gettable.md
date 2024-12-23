# Прочитать таблицу 


Элемент предназначен для чтения данных из табличного элемента управления. Для корректной работы следует помещать его в контейнер [**Открыть браузер**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_open) или [**Присоединиться к браузеру**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/el_browser_attach).

Если нажать на панели элемента кнопку **Мастер**, то откроется мастер чтения таблиц. 

![Read Table 2](<../../../.gitbook/assets/image (207).png>)

В окне мастера выберите кнопку **Захват**.

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
Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Группа «Процесс»**:

1. **Мастер** *[String]* — шаблон для поиска элемента управления (то же, что и селектор), полученный через Мастер. 
1. **Область**          — обозначение области поиска компонена.
1. **Тэг строки\*** *[String]* — тег элемента строки. Например "TH".
1. **Тэг колонки\*** *[String]* — тег элемента колонки. Например "MY".
1. **Тэг заголовка** *[String]* — тег элемента заголовка. Например "TO".
1. **Таймаут\*** *[Int32]* — предельное время ожидания завершения процесса (в миллисекундах). По умолчанию `10000`.
1. **Шаблон поиска** *[String]* — шаблон поиска элемента управления. 
1. **Элемент** *[LTools.WebBrowser.Model.IElementInfo]* — переменная со ссылкой на элемент управления. Такую переменную можно получить при помощи компонента [**Присутствие элемента**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_uiinteraction/el_exists), а потом указать ее в этом свойстве. Для этого откройте редактор кода и укажите `<название переменной>.BrowserElement`. Пример:

    ![](<../../../.gitbook/assets/execute-js-browser-element.png>)
  

**Группа «Вывод»**:

1. **Переменная** *[LTools.WebBrowser.Model.WebDataTable](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_browser/datatypes/webdatatable)]* — переменная для хранения результатов чтения таблицы.
1. **Переменная (таблица)** *[DataTable]* — переменная для хранения результатов чтения таблицы в формате System.Data.DataTable.


###  Новый мастер чтения таблиц

С версии 1.25.1 добавлен новый инструмент **Мастер чтения таблиц**. Этот инструмент позволяет эффективно настраивать, извлекать и обрабатывать данные из веб-таблиц.
**Окно "Парсинг данных"** отображает информацию о количестве извлечённых строк и столбцов. Если данные не найдены, отображается `0` строк, `0` столбцов. Содержит следующие элементы:
     - *Кнопка "Подтвердить"*: Завершает процесс извлечения с текущими настройками.
     - *Кнопка "Настройки"* (иконка шестерёнки): Открывает дополнительные параметры настройки:
              - *Сохранить в переменную* — позволяет сохранить извлечённые данные в указанную переменную.
              - *Ограничить извлечение* — устанавливает ограничения на количество строк и столбцов.
              - *Дополнительные параметры* — позволяют задать специфические настройки для точного извлечения данных.

При попытке повторно считать данные отображается диалоговое окно с предупреждением о том, что текущие параметры будут удалены. После подтверждения пользователь может выбрать новый элемент для извлечения.

#### Как использовать мастер чтения таблиц

1. В активности *Прочитать Таблицу* нажмите на кнопку "Мастер".
2. Укажите место считывания данных на экране.
3. Подтвердите процесс извлечения с текущими настройками.
4. Дождитесь завершения прогресса парсинга.
5. Проверьте предварительный результат в окне "Парсинг данных".
6. При необходимости откройте *Настройки* для уточнения параметров извлечения.
7. Подтвердите процесс, нажав кнопку "Подтвердить".
8. Если требуется повторная настройка, воспользуйтесь опцией сброса параметров и начните процесс заново.

Если необходимо воспользоваться старым мастером чтения таблиц, то перейдите в **Настройки Студии** — **Общие** — **Элементы**— Установить чек бокс **Использовать старый мастер чтения таблиц**.

## Пример использования 

Скачайте на [Learning](https://github.com/PrimoRPA/Learning) обучающий проект **StudioActivities**, чтобы просмотреть готовый RPA-процесс по работе с элементом **Прочитать таблицу**. Процесс находится по пути `StudioActivities > Ru > Браузер > Прочитать таблицу.ltw`. Откройте проект в Студии и запустите процесс.


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
