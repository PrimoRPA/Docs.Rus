---
description: Look up range
---

# Поиск в диапазоне

Элемент осуществляет поиск значения в диапазоне ячеек Excel. Результат поиска сохраняется в указанную переменную.

Путь до файла, тип драйвера и прочие параметры предварительно настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets1/WFLookUpRange.png>)

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип    | Описание                                                                                                                                  | Пример       |
| --------------- | ------ | ----------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| Значение\*      | String | Искомое значение                                                                                                                          | `"value"`    |
| Диапазон        | String | Диапазон считывания ячеек. Если не указан, будет прочитан выделенный диапазон. Если указан символ `"*"`, будет прочитан весь лист         | `"A1:D12"`   |
| Страница        | String | Наименование страницы в книге Excel                                                                                                       | `"Лист1"`    |
| Индекс страницы | Int32  | Номер страницы в книге Excel. Нумерация начинается с нуля                                                                                 | `0`          |
| Переменная      | String | Название переменной для хранения результатов поиска                                                                                       |              |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Диапазон: [String] Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон.  Если указан символ "*", будет прочитан весь лист
//text - Значение: [String] Искомое значение
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы

LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
string range = "A5:F8";
string text = "PrimoRPA";
string data = app.LookUpRange(range, text, "Лист1", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#range - Диапазон: [String] Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон.  Если указан символ "*", будет прочитан весь лист
#text - Значение: [String] Искомое значение
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы

app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx",";", LTools.Office.Model.InteropTypes.DX)
range = "A5:F8";
text = "PrimoRPA";
data = app.LookUpRange(range, text, "Лист1", 0) #string
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//range - Диапазон: [String] Диапазон считывания ячеек (A1:D12). Если не указан, будет прочитан выделенный диапазон.  Если указан символ "*", будет прочитан весь лист
//text - Значение: [String] Искомое значение
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы

let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
let range = "A5:F8";
let text = "PrimoRPA";
let data = app.LookUpRange(range, text, "Лист1", 0); //string
```
{% endtab %}
{% endtabs %}
