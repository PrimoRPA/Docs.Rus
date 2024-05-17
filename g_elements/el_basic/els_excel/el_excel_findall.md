---
description: Find all
---


# Поиск на странице

Элемент осуществляет поиск указанного значения на странице Excel. Результат сохраняется в переменную.

Путь до файла и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

![](<../../../.gitbook/assets1/WFFindAll.png>)


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип           | Описание                                   | Пример     |
| --------------- | ------------- | ------------------------------------------ | ---------- |
| **Excel:**      |               |                                            |  |
| Значение\*      | String        | Искомое значение                           | `"значение"`  |
| Страница        | String        | Наименование страницы в книге Excel        | `"Лист1"`  |
| Индекс страницы | Int32         | Номер страницы в книге Excel. Нумерация начинается с нуля | `0` |
| **Вывод:**      |               |                                            |  |
| Переменная      | List\<String> | Название переменной для записи результатов поиска |  |


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//text - Значение: [String] Искомое значение
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы

LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", LTools.Office.Model.InteropTypes.DX);
string text = "PrimoRPA";
List<string> data = app.FindAll(text, "Лист1", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
#Свойства элемента:
#app - [LTools.Office.ExcelApp] Приложение Excel
#text - Значение: [String] Искомое значение
#sheet - Страница: [String] Наименование страницы
#sheetIdx - Индекс страницы: [Int32] Индекс страницы

app = LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx",";", LTools.Office.Model.InteropTypes.DX)
text = "PrimoRPA";
data = app.FindAll(text, "Лист1", 0) #List<string>
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
//Свойства элемента:
//app - [LTools.Office.ExcelApp] Приложение Excel
//text - Значение: [String] Искомое значение
//sheet - Страница: [String] Наименование страницы
//sheetIdx - Индекс страницы: [Int32] Индекс страницы

let app = _lib.LTools.Office.ExcelApp.Init(wf, ".\\TestData.xlsx", ";", _lib.LTools.Office.Model.InteropTypes.DX);
var text = "PrimoRPA";
let data = app.FindAll(text, "Лист1", 0); //List<string>
```
{% endtab %}
{% endtabs %}
