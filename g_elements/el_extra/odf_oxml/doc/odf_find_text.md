# Найти текст

Элемент ищет вхождение заданного текста в документ. Путь до файла указывается в контейнере «Документ ODF».

![](<../../../../.gitbook/assets1/windows_items/odf-find-text.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


1. **Текст** *[String]* — искомый текст.  
2. **Переменная** *[Int32]* — переменная для хранения индекса первого вхождения текста. 
3. **Переменная (массив)** *[List\<Int32>]* — переменная для хранения массива индексов вхождения текста.


## Только код
Пример использования элемента в процессе с типом Только код (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
List<int> idxs = app.FindText(text);
int? idx = app.FindTextFirst(text);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
