# Вставка изображения

Элемент вставляет изображение в ODF-файл. Путь до файла указывается в контейнере «Документ ODF».

![](<../../../../.gitbook/assets1/windows_items/odf-input-image.png>)


## Свойства

Описание общих свойств см. в разделе [Свойства элемента](https://docs.primo-rpa.ru/primo-rpa/primo-studio/process/elements#svoistva-elementa).


1. **Изображение**\* *[byte[]]]* — изображение для вставки.  
2. **Позиция** *[Int32]* — позиция для вставки изображения. 
3. **Закладка** *[String]* — название закладки, определяющей начало записи. Если не указано, запись производится в конец текста.

## Только код
Пример использования элемента в процессе с типом **Только код** (Pure code):

C#:  
```
Primo.Office.OdfOxml.WordApp app = Primo.Office.OdfOxml.WordApp.Init(wf, "fileName");
app.InsertPicture(pic, bookmark);
app.InsertPicture(pic, pos);
```

:small_orange_diamond: *Примечание. В языках Python и JavaScript использование элемента на данный момент не реализовано.*
