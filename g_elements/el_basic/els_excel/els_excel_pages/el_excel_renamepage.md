---
description: Rename sheet
---


# Переименовать страницу

Элемент переименовывает страницу книги в Excel. Путь до файла указывается в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app)

Если требуется сохранить изменения, то дополнительно используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/osnovnye-elementy/prilozhenie-excel/el_excel_save).

![Элемент «Переименовать страницу»](<../../../../.gitbook/assets/image (41).png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Индекс\*** *[Int32]* — порядковый номер страницы, которую вы хотите переименовать. Нумерация начинается с нуля. 
1. **Имя\*** *[String]* — новое название страницы.


## Только код

Символ `*` указывает на обязательность заполнения свойства. Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.SheetRename("new name", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.SheetRename("new name", 0)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.SheetRename("new name", 0);
```
{% endtab %}
{% endtabs %}
