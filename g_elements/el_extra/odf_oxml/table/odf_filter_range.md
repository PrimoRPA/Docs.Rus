# Фильтр диапазона

*Eng: Filter range*

![](../../../../.gitbook/assets1/filterrange.png)

Компонент устанавливает фильтр диапазона ячеек таблицы.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. 
Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

**Таблица:**  
1. **Диапазон\*** *[String]* - Диапазон ячеек. Пример: `"A1:D12"`  
1. **Страница** *[String]* - Наименование страницы (работает, только когда не указан индекс страницы). Пример: `"Лист 1"`  
1. **Индекс страницы** *[Int32]* - Индекс страницы (отсчет ведется с нуля; значение по умолчанию - `0`, когда название страницы также не указано). Пример: `1`  
1. **Фильтр** *[List<string>]* - Значения фильтра. 
1. **Индекс колонки** *[Int32]* - Индекс колонки, по которой производится фильтрация (отсчет ведется с нуля; значение по умолчанию - `0`). Пример: `2`  

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.FilterRange(new List<string>(), "A1:C12", "Лист1", null,1);
```
{% endtab %}

{% tab title="Python" %}
```python
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file])
app.FilterRange(new List<string>(), "A1:C12", "Лист1", null,1)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.FilterRange(new List<string>(), "A1:C12", "Лист1", null,1);
```
{% endtab %}
{% endtabs %}
