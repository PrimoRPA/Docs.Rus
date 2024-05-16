# Сохранить документ


Элемент сохраняет текущее состояние файла. Если в свойствах данного элемента не указан путь к файлу, то сохранен будет файл, открытый в рамках контейнера «Документ ODF». 

![](<../../../../.gitbook/assets1/windows_items/odf-save.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Путь к файлу** *[String]* — путь к ODF-файлу.


## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.Save();
app.SaveAs(fileName);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
