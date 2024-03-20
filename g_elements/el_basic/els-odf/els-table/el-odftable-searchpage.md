# Поиск на странице

![](<../../../../.gitbook/assets1/Cropped-PageSearch.png>)

Компонент, осуществляющий поиск значения на странице Excel.

## Свойства
Символ `*` в названии свойства указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Значение\*** *[String]*: Искомое значение.
2. **Страница** *[String]*: Наименование страницы.
3. **Индекс страницы** *[Int32]*: Индекс страницы.
4. **Переменная** *[List<String>]*: Переменная для хранения результатов поиска.

## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
`Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);`  
`List<string> data = app.FindAll(text, [sheet], [sheetIdx]);`
