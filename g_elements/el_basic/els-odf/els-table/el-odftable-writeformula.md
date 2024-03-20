# Ввод формулы в ячейку

![](<../../../../.gitbook/assets1/Cropped-WriteFormula.png>)

Компонент, производящий запись формулы в ячейку Excel.

**Примечания**:

Если в файле требуется сохранить изменения, то после ввода формулы используйте элемент [Сохранить документ](https://docs.primo-rpa.ru/primo-rpa/g_elements/el_basic/els-odf/els-table/el-odftable-save).

## Свойства

Описание общих свойств элемента см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).\
Символ `*` в названии свойства указывает на обязательность заполнения.

1. **Страница** *[String]*: Наименование страницы Excel, на которой находится ячейка. Пример: `"List 1"`.
2. **Индекс страницы** *[Int32]*: Порядковый номер страницы. Отсчет начинается с 0. Пример: `0`.
3. **Формула\*** *[String]*: Формула, вводимая в ячейку. 
4. **Ячейка\*** *[String]*: Идентификатор ячейки. Пример: `"A1"`.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`app.WriteCellFormula(cell, text, [sheet], [sheetIdx], [numFormat]);`
