# Ввод в ячейку

![](<../../../.gitbook/assets/image (450).png>)

Производит запись данных в выбранную ячейку Excel. 

После записи данных не забудьте использовать элемент [**Сохранить документ**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_save), иначе изменения в файле не сохранятся.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

| Свойство        | Тип     | Описание                      |
| --------------- | ------- | ----------------------------- |
| Ячейка\*        | String  | Идентификатор ячейки. Пример: `"A1"`. Ячейка должна быть указана в соответствии со стилем ссылок, установленным в приложении Excel и в свойствах контейнера [**Приложение Excel**](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els_excel/el_excel_app) (см. состояние флага **R1C1**). По умолчанию используется стиль ссылок А1 |
| Данные\*        | String  | Данные, вводимые в ячейку. Может быть использована строковая переменная     |
| Страница        | String  | Наименование страницы         |
| Индекс страницы | Int32   | Индекс страницы - порядковый номер листа в книге Excel. Отсчет начинается с 0 |
| Как текст       | Boolean | Определите, нужно ли вставлять значение, как текст |
| Числовой формат | String  | Формат вводимого числа (#,#)  |

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
