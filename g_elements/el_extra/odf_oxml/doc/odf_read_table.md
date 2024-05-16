# Прочитать таблицу

Элемент читает таблицу из документа и сохраняет в переменную. Путь до файла указывается в контейнере «Документ ODF».

![](<../../../../.gitbook/assets1/windows_items/odf-read-table.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Индекс\*** *[Int32]* — порядковый номер таблицы в документе.
2. **Таблица** *[System.Data.DataTable]* — переменная для хранения прочитанной таблицы. 
3. **Данные** *[List\<List\<String>>]* — переменная для хранения прочитанной таблицы. Отличается от свойства «Таблица» только типом данных.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");   
List<List<string>> list = app.ReadTableArr(idx);
System.Data.DataTable table = app.ReadTable(idx);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
