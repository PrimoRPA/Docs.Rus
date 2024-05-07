---
description: Change cells
---

# Изменение ячейки

![](<../../../../.gitbook/assets1/Cropped-WriteFormula.png>)

Компонент, изменяющий формат ячеек в таблице.

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Диапазон** *[String]*: Диапазон ячеек. Пример: `A1:D12`.
2. **Страница** *[String]*: Название страницы (работает только когда не указан индекс страницы). Пример: `"Лист 1"`
3. **Индекс страницы** *[Int32]*: Индекс страницы (отсчет ведется с нуля; значение по умолчанию - `0`, когда название страницы также не указано). Пример: `1` 
4. **Цвет ячеек** *[Sуstem.Drawing.Color?]*: Цвет ячеек диапазона. Пример: `System.Drawing.Color.LightBlue`.
5. **Цвет бордюра** *[Sуstem.Drawing.Color?]*: Цвет бордюра ячеек диапазона. Пример: `System.Drawing.Color.Black`.
6. **Тип бордюра** *[Primo.Office.OdfOxml.Model.CellBorderTypes]*: Определяет бордюр ячеек для изменения. Пример: `Primo.Office.OdfOxml.Model.CellBorderTypes.Around` 
7. **Толщина бордюра** *[Primo.Office.OdfOxml.Model.CellBorderThickness]*: Толщина бордюра ячеек. Пример: `Primo.Office.OdfOxml.Model.CellBorderThickness.Medium`

### Примечание
Свойство **Тип бордюра** может принимать следующие значения:<br>

- Keep: не изменять границы
- None: удалить все границы ячеек
- Around: внешняя граница диапазона
- Full: все границы ячеек
- Left: левая граница диапазона
- Right: правая граница диапазона
- Top: верхняя граница диапазона
- Bottom: нижняя граница диапазона
- Vertical: вертикальные границы ячеек       
- Horizontal: горизонтальные границы ячеек
 
Свойство **Толщина бордюра** может принимать следующие значения:<br>
- Thin: тонкий
- Medium: средний
- Thick: толстый

### Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

{% tabs %}
{% tab title="C#" %}
```csharp
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.SetCells("A1:D12",System.Drawing.Color.LightBlue, System.Drawing.Color.Black, Model.CellBorderThickness.Medium, Model.CellBorderTypes.Around, [sheet], [sheetIdx]);
```
{% endtab %}

{% tab title="Python" %}
```python
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file])
app.SetCells("A1:D12",System.Drawing.Color.LightBlue, System.Drawing.Color.Black, Model.CellBorderThickness.Medium, Model.CellBorderTypes.Around, [sheet], [sheetIdx])
```
{% endtab %}

{% tab title="JavaScript" %}
```javascript
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.SetCells("A1:D12",System.Drawing.Color.LightBlue, System.Drawing.Color.Black, Model.CellBorderThickness.Medium, Model.CellBorderTypes.Around, [sheet], [sheetIdx]);
```
{% endtab %}
{% endtabs %}
