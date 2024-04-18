---
description: Save workbook
---

# Сохранить документ

![](<../../../.gitbook/assets/image (283).png>)

Элемент сохраняет текущее состояние файла Excel. 

Поддерживаемые расширения:
* XLSX — стандартный формат файлов Excel 2010 и Excel 2007, основанный на языке XML. В этом формате нельзя сохранять код макросов Microsoft Visual Basic для приложений (VBA) и листы макросов Microsoft Office Excel 4.0 (XLM).
* XLSM — формат файлов на основе XML и с поддержкой макроса для Excel 2016, Excel 2013, Excel 2010 и Excel 2007. В этом формате можно сохранять код макросов VBA и листы макросов Excel 4.0 (XLM).
* XLSB — формат двоичных файлов (BIFF12) для Excel 2010 и Excel 2007. Поддерживает макросы.
* XLS — формат двоичных файлов, который использовался по умолчанию в ранних версиях Excel (97-2003). 
* CVS — сохраняет книгу (только активный лист) в виде текстового файла с разделителями. Вид разделителя указывается в свойстве **Разделитель** в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app). 

:small_blue_diamond: ***Примечание**. Когда вы сохраняете файл в другом формате, часть форматирования, данных и функций может быть потеряна.*


## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство     | Тип    | Описание                                  | Пример          |
| ------------ | ------ | ----------------------------------------- | --------------- |
| **Excel:**   | | | |
| Путь к файлу | String | Путь к файлу Excel. Если значение не задано, то документ будет сохранен по пути, указанному в текущем контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app) | `@"C:\folder\files.xlsx"` |


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file2");
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.Save()
app.SaveAs("file")
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.Save();
app.SaveAs("file");
```
{% endtab %}
{% endtabs %}
