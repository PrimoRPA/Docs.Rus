# Таблицу в CSV

*Eng: Table to CSV*

[](<../../../.gitbook/assets/image (100) (1) (1) (1) (1) (1) (1) (1) (2) (107).png>)

Элемент позволяет экспортировать данные из таблицы в формат CSV.

![](<../../../.gitbook/assets/image (435).png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


**Группа «Управление коллекцией»**:
 
* **Разделитель\***: String. Символ или последовательность символов, используемые для разделения колонок в CSV. По умолчанию задан разделитель `";"`  (точка с запятой). Возможно указать и другие значения - `","`, `":"`  и т. д.  Выбранный разделитель должен быть уникальным и не использоваться внутри значений в таблице. Иначе это может привести к некорректному разделению значений и сдвигу таблицы.
* **Таблица\***: [System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-7.0). Таблица, которую необходимо экспортировать. Указывается в виде переменной.


**Группа «Вывод»**:

* **Переменная\***: String. Переменная для сохранения результатов преобразования.

## Пример на Learning

На странице [Learning](https://github.com/PrimoRPA/Learning) доступен RPA-проект, обучающий работе с элементом:

1. Скачайте архив со всеми обучающими материалами.
2. Распакуйте архив и откройте в Студии проект **StudioActivities**.
3. Выберите процесс `StudioActivities/Ru/Коллекции/Таблицу в CSV.ltw` для просмотра.


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
