---
description: Add sheet
---

# Добавить страницу

Элемент создает страницу в книге Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

Если изменения требуется сохранить, то дополнительно используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/el_excel_save).

![](<../../../../.gitbook/assets1/windows_items/ExcelWFSheetAdd.png>)



## Свойства

Символ `*` указывает на обязательность заполнения свойства. Описание общих свойств см. [здесь](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Имя\*** *[String]* — название будущей страницы. Пример: `"List2"`.
1. **Индекс** *[Int32]* — порядковый номер будущей страницы. Нумерация начинается с нуля.  Пример: `1`.


## Только код

Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SheetAdd("new page", 3);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SheetAdd("new page", 3)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SheetAdd("new page", 3);
```
{% endtab %}
{% endtabs %}
