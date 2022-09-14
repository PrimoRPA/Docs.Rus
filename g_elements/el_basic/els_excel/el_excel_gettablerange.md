# Получение диапазона таблицы

![](<../../../.gitbook/assets/Получение диапазона таблицы.png>)

Предназначен для получения диапазона таблицы Excel.

> *Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*.

| Свойство        | Тип    | Описание               |
| --------------- | ------ | ---------------------- |
| Таблица\*       | String | Название таблицы       |
| Диапазон\*      | String | Диапазон таблицы       |
| Страница        | String | Название страницы      |
| Индекс страницы | Int32  | Индекс страницы        |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, @"c:\file.xlsx");
string data = app.GetTableRange("table name");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "c:\file.xlsx")
data = app.GetTableRange("table name")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "c:\\file.xlsx");
var data = app.GetTableRange("table name");
```
{% endtab %}
{% endtabs %}

