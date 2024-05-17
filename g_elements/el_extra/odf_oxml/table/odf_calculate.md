# Пересчет формул

Элемент пересчитывает формулы на листах ODF-файла. Путь до файла указывается в контейнере «Таблица ODF».

![Элемент «Пересчет формул»](<../../../../.gitbook/assets1/windows_items/odf-calculate.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

Специальных свойств данный элемент не имеет.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):  

**C#**  
```
Primo.Office.OdfOxml.ExcelApp app = Primo.Office.OdfOxml.ExcelApp.Init(wf, [file]);
app.Calculate();
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
