# Чтение текста

Элемент считывает данные из документа и сохраняет результат в переменную. Путь до файла указывается в контейнере «Документ ODF».

![](<../../../../.gitbook/assets1/windows_items/odf-read-text.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).

1. **Переменная\*** *[String]* — переменная для хранения результатов чтения.
2. **Начало** *[Int32]* — начало выделения текста.
3. **Длина** *[Int32]* — длина выделения текта.   


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
string txt = app.ReadText([selStart], [selLength]);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*

