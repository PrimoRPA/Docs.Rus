# Таблицу в CSV

*Eng: Table to CSV*

[](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (107).png>)

Элемент предназначен для экспорта данных из таблицы в формат CSV.

![](<../../../.gitbook/assets/image (435).png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


**Группа «Управление коллекцией»**:
 
1. **Разделитель\***: String. Символ или последовательность символов, используемые для разделения колонок в CSV. По умолчанию задан разделитель `";"`  (точка с запятой). Возможно указать и другие значения - `","`, `":"`  и т. д.  Выбранный разделитель должен быть уникальным и не использоваться внутри значений в таблице. Иначе это может привести к некорректному разделению значений и сдвигу таблицы.
2. **Таблица\***: [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-7.0). Таблица, которую необходимо экспортировать. Указывается в виде переменной.


**Группа «Вывод»**:

1. **Переменная\***: String. Переменная для сохранения результатов преобразования.

## Пример на Learning

RPA-проект, демонстрирующий работу элемента, доступен на [Learning](https://github.com/PrimoRPA/Learning/tree/master). Скачайте проект StudioActivities, откройте его в Студии и выберите процесс `StudioActivities/Ru/Коллекции/Таблицу в CSV.ltw` для просмотра. Процесс имеет тип **Последовательность**.

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
