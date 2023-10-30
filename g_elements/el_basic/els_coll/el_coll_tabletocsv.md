# Таблицу в CSV

*Eng: Table to CSV*

![](<../../../.gitbook/assets/image (435).png>)

Данный компонент предназначен для экспорта данных из таблицы в формат CSV

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


**Группа «Коллекция»**:

1. **Разделитель\***. String. Символ или последовательность символов, используемые для разделения колонок в CSV. Пример: `Пример: ";" ","`.
2. **Таблица\***. System.Data.DataTable.Таблица данных, которую необходимо экспортировать. 


**Группа «Выходные данные»**:

1. **Переменная\***. String. Переменная для сохранения результатов преобразования.

## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
System.Data.DataTable table = new System.Data.DataTable();
string ret = LTools.Common.Helpers.DataHelper.DataTableToCSV(table, ";");
```
{% endtab %}

{% tab title="Python" %}
```python
table = System.Data.DataTable()
ret = LTools.Common.Helpers.DataHelper.DataTableToCSV(table, ";")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var table = host.newObj(_lib.System.Data.DataTable);
var ret = _lib.LTools.Common.Helpers.DataHelper.DataTableToCSV(table, ";");
```
{% endtab %}
{% endtabs %}
