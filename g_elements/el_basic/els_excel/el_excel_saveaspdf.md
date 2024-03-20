# Сохранить как PDF

![](<../../../.gitbook/assets/Сохранить как PDF.png>)

Элемент работает внутри контейнера [**Приложение Excel**](https://docs.primo-rpa.ru/primo-rpa/g\_elements/el\_basic/els\_excel/el\_excel\_app) и позволяет экспортировать файл, указанный в элементе приложения, в формат PDF.

> _Описание общих свойств см. в разделе_ [_**Работа с элементами**_](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements).

| Свойство                  | Тип     | Описание                                                                                                                                     |
| ------------------------- | ------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Путь                      | String  | Путь до места сохранения PDF-файла. Пример: С:\folder\file.pdf                                                                               |
| Заменять существующий     | Boolean | Установка флага позволяет пересохранить уже существующий файл PDF                                                                            |
| Индекс первой страницы    | Int32   | Если экспортировать нужно не все страницы файла Excel, задайте диапазон: укажите номер первой страницы для сохранения. Отсчет начинается с 0 |
| Индекс последней страницы | Int32   | Номер последней страницы для сохранения                                                                                                      |
| Мин. качество             | Boolean | Минимальное качество выходного файла                                                                                                         |

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, @"c:\file.xlsx");
app.ExportToPdf(@"c:\file.pdf", true, false)
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "c:\file.xlsx")
app.ExportToPdf("c:\file.pdf", true, false
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "c:\\file.xlsx");
app.ExportToPdf("c:\\file.pdf", true, false);
```
{% endtab %}
{% endtabs %}
