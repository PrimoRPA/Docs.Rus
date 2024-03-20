# Получение диапазона таблицы

Элемент помогает вычислить диапазон таблицы по ее названию. 

![](<../../../.gitbook/assets/Получение диапазона таблицы.png>)

Под таблицей в Excel подразумевается диапазон ячеек, отформатированый в виде таблицы для того, чтобы легче было управлять группой связанных данных. Подробнее о понятии **Таблица** читайте [здесь](https://support.microsoft.com/ru-ru/office/%D0%BE%D0%B1%D1%89%D0%B8%D0%B5-%D1%81%D0%B2%D0%B5%D0%B4%D0%B5%D0%BD%D0%B8%D1%8F-%D0%BE-%D1%82%D0%B0%D0%B1%D0%BB%D0%B8%D1%86%D0%B0%D1%85-excel-7ab0bb7d-3a9e-4b56-a3c9-6c94334e492c).


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание               |
| --------------- | ------ | ---------------------- |
| Таблица\*       | String | Название таблицы       |
| Диапазон\*      | String | Диапазон таблицы       |
| Страница        | String | Название страницы      |
| Индекс страницы | Int32  | Индекс страницы        |

## Только код

Ниже приведен пример использования элемента в процессе с типом **Только код** (Pure code):

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

