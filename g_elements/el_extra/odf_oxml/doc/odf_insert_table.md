# Вставить таблицу

Элемент вставляет таблицу в документ. Путь до файла указывается в контейнере «Документ ODF».

![](<../../../../.gitbook/assets1/windows_items/odf-input-table.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


1. **Таблица** *[[System.Data.DataTable](https://learn.microsoft.com/ru-ru/dotnet/api/system.data.datatable?view=net-5.0)]* — название переменной с типом DataTable, содержащей таблицу с данными для вставки.  
2. **Данные** *[List<List\<string>>]* — данные таблицы для вставки. В отличие от свойства «Таблица», в этом свойстве данные указываются в виде переменной с типом список списков строк. 
3. **Закладка** *[String]* — название закладки, определяющей начало записи. Если не указано, запись производится в конец текста.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.InsertTable(data, [bookmark]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
