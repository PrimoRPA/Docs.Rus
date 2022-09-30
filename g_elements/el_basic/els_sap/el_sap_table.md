# Таблица

![](<../../../.gitbook/assets/image (413).png>)

Элемент, получающий указатель на UI-элемент Таблица.

| Свойство                    | Тип                                                                       | Описание                                                              |
| --------------------------- | ------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| Окно        | String                     | Позволяет выбрать окно программы, с которым необходимо работать. Укажите заголовок окна |
| ID элемента                 | String                                                                    | ID элемента                                                           |
| Элемент                     | LTools.SAP.Model.SAPUIItem                                                | Ссылка на элемент управления                                          |
| Таблица                     | [LTools.SAP.Model.SAPUIGrid](datatypes/sapuigrid.md)                      | Переменная, хранящая ссылку на таблицу                                |
| Полное чтение               | bool                                                                      | Признак полного чтения данных таблицы, включая чек-боксы, цвет и т.д. |
| Переменная                  | [LTools.SAP.Model.SAPUIGrid](datatypes/sapuigrid.md)                      | Переменная для сохранения ссылки на таблицу                           |
| Ячейки                      | List\<List<[LTools.SAP.Model.SAPUIGridCell](datatypes/sapuigridcell.md)>> | Значения ячеек таблицы                                                |
| Ячейки (Таблица)            | System.Data.DataTable                                                     | Значения ячеек таблицы                                                |
| Колонки                     | List<[LTools.SAP.Model.SAPUIGridColumn](datatypes/sapuigridcolumn.md)>    | Информация о колонках таблицы                                         |
| Выбранные строки            | List\<int>                                                                | Массив индексов выбранных строк                                       |
| Выбранные ячейки            | Dictionary\<int, string>                                                  | Массив выбранных ячеек                                                |
| Выбрать строки              | List\<int>                                                                | Массив строк для выбора                                               |
| Выбрать ячейки              | List\<string>                                                             | Массив ячеек для выбора                                               |
| Клик                        | Dictionary\<int, string>                                                  | Клик ячейки                                                           |
| Двойной клик                | Dictionary\<int, string>                                                  | Двойной клик ячейки                                                   |
| Выбрать текущую ячейку      | String                                                                    | Выбрать текущую ячейку 'индекс, ключ колонки'                         |
| Клик текущей ячейки         | bool                                                                      | Клик текущей ячейки                                                   |
| Двойной клик текущей ячейки | bool                                                                      | Двойной клик текущей ячейки                                           |
| Кнопка текущей ячейки       | bool                                                                      | Нажатие кнопки текущей ячейки                                         |
| Кнопка управления           | String                                                                    | Клик кнопки управления по идентификатору                              |
| Горизонтальная              | int?                                                                      | Горизонтальная прокрутка                                              |
| Вертикальная                | int?                                                                      | Вертикальная прокрутка                                                |
| Прокрутка                   | System.Drawing.Point                                                      | Текущее состояние прокрутки                                           |
| Лимит прокрутки             | System.Drawing.Point                                                      | Предельное значение прокрутки                                         |
| Нажать F4                   | bool                                                                      | Нажать кнопку F4                                                      |
| Нажать Enter                | bool                                                                      | Нажать кнопку Enter                                                   |
| Вставить строки             | String                                                                    | Вставить строки '0,1,5' либо '\*' для вставки в конец                 |
| Удалить строки              | String                                                                    | Удаляет строки '0,1,5'                                                |
| Изменить значение           | String                                                                    | Изменяет значение ячейки 'индекс, ключ колонки, значение'             |
| Таймаут\*                   | Int32                                                                     | Предельное время ожидания завершения процесса (мс)                    |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.SAP.SapApp app = LTools.SAP.SapApp.Init(wf);
LTools.SAP.Model.SAPUIGrid tbl = app.Table("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
tbl.SelectRows(new List<int>() { 1 });
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.SAP.SapApp.Init(wf)
tbl = app.Table("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell")
tbl.SelectRows(List[int]([ 1 ]))
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var host = new _lib.Microsoft.ClearScript.HostFunctions();
var app = _lib.LTools.SAP.SapApp.Init(wf);		
var tbl = app.Table("/app/con[0]/ses[0]/wnd[0]/usr/cntlIMAGE_CONTAINER/shellcont/shell/shellcont[0]/shell");
var idx = host.newObj(_lib.System.Collections.Generic.List(_lib.System.Int32));
idx.Add(1);
tbl.SelectRows(idx);
```
{% endtab %}
{% endtabs %}

