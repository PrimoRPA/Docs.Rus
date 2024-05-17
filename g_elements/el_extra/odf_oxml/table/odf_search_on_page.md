# Поиск на странице

Элемент ищет значения на странице файла с ODF-таблицей. Путь до файла указывается в контейнере «Таблица ODF».

![Элемент «Поиск на странице»](<../../../../.gitbook/assets1/windows_items/odf-find-all.png>)


## Свойства

Символ `*` указывает на обязательность заполнения. Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Значение\*** *[String]* — искомое значение.
1. **Страница** *[String]* — наименование страницы.
1. **Индекс страницы** *[Int32]* — индекс страницы.
1. **Переменная** *[List<String>]* — переменная для хранения результатов поиска.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
```
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
List<string> data = app.FindAll(text, [sheet], [sheetIdx]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
