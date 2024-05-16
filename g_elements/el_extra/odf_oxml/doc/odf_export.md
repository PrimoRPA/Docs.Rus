# Экспортировать документ

Элемент экспортирует ODF-файл в указанный формат. На данный момент поддерживает экспорт только в PDF. 

![](<../../../../.gitbook/assets1/windows_items/odf-export.png>)



## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Путь к файлу** *[String]* — путь к файлу.
2. **Формат** *[LTools.Office.Model.WordExportFormats]* — тип формата. На данный момент только PDF. 


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.Export(fileName, [format]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
