# Получение диапазона таблицы

![](<../../../.gitbook/assets/Получение диапазона таблицы.png>)

Предназначен для получения диапазона таблицы Excel.

*Описание общих свойств см. в разделе [**Работа с элементами**](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements)*.

| Свойство        | Тип    | Описание               |
| --------------- | ------ | ---------------------- |
| Таблица\*       | String | Название таблицы       |
| Диапазон\*      | String | Диапазон таблицы       |
| Страница        | String | Название страницы      |
| Индекс страницы | Int32  | Индекс страницы        |
=======
Под таблицей в Excel подразумевается диапазон ячеек, отформатированый в виде таблицы для того, чтобы легче было управлять группой связанных данных. Подробнее о понятии **Таблица** читайте [здесь](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D1%89%D0%B8%D0%B5-%D1%81%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BE-%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%D1%85-excel-7ab0bb7d-3a9e-4b56-a3c9-6c94334e492c).

Данный элемент помогает вычислить диапазон таблицы по ее названию.

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

