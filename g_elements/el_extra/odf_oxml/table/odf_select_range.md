# Выделение диапазона

Элемент выделяет диапазон ячеек в в ODF-таблице. Путь до файла указывается в контейнере «Таблица ODF».

![Элемент «Выделение диапазона»](<../../../../.gitbook/assets1/windows_items/odf-select-range.png>)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Диапазон\*** *[String]* — диапазон считывания ячеек.
1. **Страница** *[String]* — наименование страницы c таблицей.
1. **Индекс страницы** *[Int32]* — индекс страницы c таблицей.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#** 
```
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.SelectRange(range, [sheet], [sheetIdx]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
