---
description: Cell input
---

# Ввод в ячейку

Элемент записывает данные в выбранную ячейку Excel. Путь до файла, тип драйвера и другие базовые параметры настраиваются в контейнере [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app).

После записи данных используйте элемент [**Сохранить документ**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save), иначе изменения в файле не сохранятся.

![](<../../../.gitbook/assets1/WFWriteCell.png>)

## Свойства

Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

| Свойство        | Тип     | Описание                      | Пример       |
| --------------- | ------- | ----------------------------- | ------------ |
| Ячейка\*        | String  | Идентификатор ячейки. Ячейка должна быть указана в соответствии со стилем ссылок, установленным в приложении Excel и в свойствах контейнера [Приложение Excel](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app) (см. состояние флага **R1C1**). По умолчанию используется стиль ссылок А1 | `"A1"` |
| Данные\*        | String  | Данные, вводимые в ячейку                                         | `"data"`  |
| Страница        | String  | Наименование страницы в книге Excel                               | `"Лист1"` |
| Индекс страницы | Int32   | Порядковый номер листа в книге Excel. Нумерация начинается с нуля | `0`       |
| Как текст       | Boolean | Определяет, нужно ли вставить значение, как текст                 |           |
| Числовой формат | String  | Формат вводимого числа                                            | `#,#`     |

## Только код

Пример использования элемента в процессе с типом **Только код (Pure code)**:

{% tabs %}
{% tab title="C#" %}
```csharp
LTools.Office.ExcelApp app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX);
app.WriteCell("A1", "text", "Лист1", 0);
```
{% endtab %}

{% tab title="Python" %}
```python
app = LTools.Office.ExcelApp.Init(wf, "file", ";", LTools.Office.Model.InteropTypes.DX)
app.WriteCell("A1", "text", "Лист1", 0)
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
var app = _lib.LTools.Office.ExcelApp.Init(wf, "file", ";", _lib.LTools.Office.Model.InteropTypes.DX);
app.WriteCell("A1", "text", "Лист1", 0);
```
{% endtab %}
{% endtabs %}
